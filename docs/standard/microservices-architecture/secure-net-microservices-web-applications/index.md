---
title: 保护 .NET 微服务和 Web 应用程序
description: .NET 微服务和 Web 应用中的安全性 - 了解 ASP.NET Core Web 应用中的身份验证选项。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 3e2598f58bf2fb34a7ad7c107066d34e0e7c3408
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464809"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>确保 .NET 微服务和 Web 应用的安全性

微服务和 Web 应用的安全性具有许多方面，该主题可能需要许多本此类书籍才能描述完，因此在本部分中，我们将重点介绍身份验证、授权和应用程序密钥。

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>在 .NET 微服务和 Web 应用中实施身份验证

通常有必要将服务发布的资源和 API 限制为特定受信任的用户或客户端。 制定有关这些种类的 API 级别信任决策的第一步是身份验证。 身份验证是可靠验证用户标识的流程。

在微服务方案中，通常会集中处理身份验证。 如果使用 API 网关，则网关是一个进行身份验证的好方法，如图 9-1 所示。 如果使用此方法，请确保在不使用 API 网关的情况下，无法直接访问各个微服务，除非其他安全性措施已就绪，可对来自网关和其他位置的消息进行身份验证。

![当 API 网关集中身份验证时，它会在向微服务转发请求时添加用户信息。](./media/image1.png)

**图 9-1**。 使用 API 网关进行集中身份验证

如果可以直接访问服务，则身份验证服务（如 Azure Active Directory）或充当安全令牌服务 (STS) 的专用身份验证微服务可用于对用户进行身份验证。 通过安全令牌或 cookie 在服务之间共享信任决策。 （如有需要，可通过实现 [Cookie 共享](/aspnet/core/security/cookie-sharing)在 ASP.NET Core 应用程序之间共享这些令牌。）此模式如图 9-2 所示。

![直接访问微服务时，包含身份验证和授权的信任由微服务之间共享的专用微服务颁发的安全令牌处理。](./media/image2.png)

**图 9-2**。 通过标识微服务进行的身份验证；使用授权令牌共享信任

### <a name="authenticate-with-aspnet-core-identity"></a>使用 ASP.NET Core 标识进行身份验证

在 ASP.NET Core 中用于标识应用程序用户的主要机制是 [ASP.NET Core 标识](/aspnet/core/security/authentication/identity)成员身份系统。 ASP.NET Core 标识会将用户信息（包括登录信息、角色和声明）存储在由开发人员配置的数据存储中。 通常情况下，ASP.NET Core 标识数据存储是 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 包中提供的实体框架存储。 但是，自定义存储或其他第三方包可用于将标识信息存储在 Azure 表存储、CosmosDB 或其他位置。

下面的代码来自选中单个用户帐户身份验证的 ASP.NET Core Web 应用程序项目模板。 它演示如何使用 Startup.ConfigureServices 方法中的 EntityFramework.Core 配置 ASP.NET Core 标识。

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

配置 ASP.NET Core 标识后，可以通过调用服务的 `Startup.Configure` 方法中的 app.UseIdentity，启用该标识。

使用 ASP.NET Core 标识可支持多个方案：

- 使用 UserManager 类型 (userManager.CreateAsync) 创建新用户信息。

- 使用 SignInManager 类型对用户进行身份验证。 可以使用 `signInManager.SignInAsync` 直接登录，或使用 `signInManager.PasswordSignInAsync` 确认用户密码正确并登录。

- 根据存储在 cookie（由 ASP.NET Core 标识中间件读取）中的信息标识用户，这样浏览器的后续请求中将包括已登录用户的标识和声明。

ASP.NET Core 标识还支持[双因素身份验证](/aspnet/core/security/authentication/2fa)。

对于使用本地用户数据存储并使用 cookie 保留请求间的标识（对于 MVC Web 应用程序是常见的）的身份验证方案，ASP.NET Core 标识是推荐的解决方案。

### <a name="authenticate-with-external-providers"></a>使用外部提供程序进行身份验证

ASP.NET Core 还支持使用[外部身份验证提供程序](/aspnet/core/security/authentication/social/)，使用户通过 [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) 流登录。 这意味着用户可从 Microsoft、Google、Facebook 或 Twitter 等提供程序中使用现有身份验证流程登录，并将这些标识与应用程序中的 ASP.NET Core 标识相关联。

若要使用外部身份验证，请在应用程序的 HTTP 请求处理管道中包括相应的身份验证中间件。 此中间件负责处理从身份验证提供程序返回 URI 路由的请求，捕获标识信息，并实现通过 SignInManager.GetExternalLoginInfo 方法提供该信息。

下表显示常用的外部身份验证提供程序及其关联的 NuGet 包：

| **提供程序**  | **包**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

在所有情况下，中间件注册与 `Startup.Configure` 中的 `app.Use{ExternalProvider}Authentication` 类似的对注册方法的调用。 根据提供程序的需要，这些注册方法会采用包含应用程序 ID 和机密信息（例如密码）的选项对象。 外部身份验证提供程序要求注册应用程序（如 [ASP.NET Core 文档](/aspnet/core/security/authentication/social/)所述），以便通知用户哪些应用程序正在请求访问其标识。

在 `Startup.Configure` 中注册中间件后，即可提示用户通过任何控制器操作进行登录。 若要执行此操作，可以创建 `AuthenticationProperties` 对象，其中包含身份验证提供程序的名称和重定向 URL。 随后，可返回一个传递 `AuthenticationProperties` 对象的质询响应。 下面的代码显示此响应的示例。

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

redirectUrl 参数包括用户通过身份验证后，外部提供程序应重定向到的 URL。 该 URL 应表示基于外部标识信息使用户登录的操作，如以下简化示例所示：

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

在 Visual Studio 中创建 ASP.NET 代码 Web 应用程序项目时，如果选择“单个用户帐户”身份验证选项，则使用外部提供程序进行登录所需的所有代码已在项目中，如图 9-3 所示。

![新 ASP.NET Core Web 应用的对话框，突出显示用于更改身份验证的按钮。](./media/image3.png)

**图 9-3**。 创建 Web 应用程序项目时，选择一个用于使用外部身份验证的选项

除了之前列出的外部身份验证提供程序外，还提供第三方包，其中提供可用于使用多个外部身份验证提供程序的中间件。 有关列表，请参阅 GitHub 上的 [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) 存储库。

也可以创建自己的外部身份验证中间件以满足一些特殊需求。

### <a name="authenticate-with-bearer-tokens"></a>使用持有者令牌进行身份验证

使用 ASP.NET Core 标识（或标识加外部身份验证提供程序）进行身份验证，这适用于应在 cookie 中存储用户信息的许多 Web 应用程序方案。 但是，在其他方案中，cookie 不是保留和传输数据的自然方式。

例如，在公开 Single Page Application (SPA)、本机客户端、甚至是其他 Web API 可能访问的 RESTful 终结点的 ASP.NET Core Web API 中，通常需要改为使用持有者令牌身份验证。 这些类型的应用程序不能与 cookie 配合使用，但可以轻松地检索持有者令牌，并将其包括在后续请求的授权标头中。 若要启用令牌身份验证，ASP.NET Core 支持几个用于使用 [OAuth 2.0](https://oauth.net/2/) 和 [OpenID Connect](https://openid.net/connect/) 的选项。

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>使用 OpenID Connect 或 OAuth 2.0 标识提供程序进行身份验证

如果用户信息存储在 Azure Active Directory 或其他支持 OpenID Connect 或 OAuth 2.0 的标识解决方案中，则可以使用 Microsoft.AspNetCore.Authentication.OpenIdConnect 包，通过 OpenID Connect 工作流进行身份验证。 例如，如果要对 eShopOnContainers 中的 Identity.Api microservice 进行身份验证，ASP.NET Core Web 应用可以使用该包中的中间件，如 `Startup.cs` 中的以下简化示例所示：

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

请注意，使用此工作流时，不需要 ASP.NET Core 标识中间件，因为所有的用户信息存储和身份验证均由标识服务处理。

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>从 ASP.NET Core 服务颁发安全令牌

如果希望为本地 ASP.NET Core 标识用户颁发安全令牌，而不是使用外部标识提供程序，可利用一些优秀的第三方库。

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) 和 [OpenIddict](https://github.com/openiddict/openiddict-core) 是 OpenID Connect 提供程序，可轻松地与 ASP.NET Core 标识集成，使用户能够从 ASP.NET Core 服务颁发安全令牌。 [IdentityServer4 文档](https://identityserver4.readthedocs.io/en/latest/)具有有关如何使用库的详细说明。 但是，使用 IdentityServer4 颁发令牌的基本步骤如下所示。

1. 调用 Startup.Configure 方法中的 app.UseIdentityServer，将 IdentityServer4 添加到应用程序的 HTTP 请求处理管道。 这使库能够为指向 OpenID Connect 和 OAuth2 终结点（如 /connect/token）的请求提供服务。

2. 通过调用 services.AddIdentityServer，配置 Startup.ConfigureServices 中的 IdentityServer4。

3. 通过设置以下数据，配置标识服务器：

   - 用于签名的[凭据](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)。

   - 用户可能会请求访问的[标识和 API 资源](https://identityserver4.readthedocs.io/en/latest/topics/resources.html)：

      - API 资源表示用户可通过访问令牌访问的受保护数据或功能。 API 资源的一个示例是要求授权的 Web API（或 API 集）。

      - 标识资源表示提供给客户端进行用户识别的信息（声明）。 声明可能包括用户名称、电子邮件地址等。

   - 为请求令牌而连接的[客户端](https://identityserver4.readthedocs.io/en/latest/topics/clients.html)。

   - 用户信息的存储机制，如 [ASP.NET Core 标识](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html)或一种替代方法。

为要使用的 IdentityServer4 指定客户端和资源时，可以将相应类型的 <xref:System.Collections.Generic.IEnumerable%601> 集合传递到采用内存中客户端或资源存储的方法中。 或者对于更复杂的方案，可以通过依赖项注入提供客户端或资源提供程序类型。

IdentityServer4 使用自定义 IClientStore 类型提供的内存中资源和客户端的示例配置可能类似于以下示例：

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>使用安全令牌

针对 OpenID Connect 终结点进行身份验证或自行颁发安全令牌会涵盖一些方案。 但对于某个服务，如果它只需限制对具有由其他服务提供的有效安全令牌的用户的访问，该怎么办？

对于这种情况，Microsoft.AspNetCore.Authentication.JwtBearer 包中提供处理 JWT 令牌的身份验证中间件。 JWT 代表“[JSON Web 令牌](https://tools.ietf.org/html/rfc7519)”，是适用于传递安全声明的通用安全令牌格式（由 RFC 7519 定义）。 如何通过中间件使用此类令牌的简化示例可能如以下代码片段（取自 eShopOnContainers 的 Ordering.Api 微服务）所示。

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

此用法的参数包括：

- `Audience` 表示传入令牌的接收方或令牌授予访问权限的资源。 如果此参数中指定的值与令牌中的参数不匹配，则会拒绝该令牌。

- `Authority` 是颁发令牌的身份验证服务器的地址。 JWT 持有者身份验证中间件使用此 URI 获取可用于验证令牌签名的公钥。 该中间件还确认令牌中的 `iss` 参数是否与此 URI 匹配。

另一个参数 `RequireHttpsMetadata` 用于测试目的；将此参数设置为 false，可在你没有证书的环境中进行测试。 在实际部署中，JWT 持有者令牌应始终只能通过 HTTPS 传递。

此中间件准备就绪后，会自动从授权标头中提取 JWT 令牌。 然后对其进行反序列化、验证（使用 `Audience` 和 `Authority` 参数的值），并将其存储为用户信息，稍后供 MVC 操作或授权筛选器引用。

JWT 持有者身份验证中间件还可以支持更高级的方案，例如颁发机构不可用时使用本地证书验证令牌。 对于此情景，可以在 `JwtBearerOptions` 对象中指定 `TokenValidationParameters` 对象。

## <a name="additional-resources"></a>其他资源

- **在应用程序之间共享 cookie** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **标识简介** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson。使用短信的双因素身份验证** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **启用使用 Facebook、Google 和其他外部提供程序的身份验证** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas。OAuth 2 简介** \
  [https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- **AspNet.Security.OAuth.Providers**（ASP.NET OAuth 提供程序的 GitHub 存储库）\
  [https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- **Danny Strockis。将 Azure AD 集成到 ASP.NET Core Web 应用中** \
  [https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- **IdentityServer4。官方文档** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[上一页](../implement-resilient-applications/monitor-app-health.md)
>[下一页](authorization-net-microservices-web-applications.md)
