---
title: 验证密码复杂性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824931"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>演练：验证密码是否复杂 (Visual Basic)
此方法检查某些强密码特性，并使用有关检查密码失败的信息更新的字符串参数。  
  
 若要授权的用户，可以安全系统中使用密码。 但是，密码必须是未经授权的用户来猜测很难。 攻击者可以使用*字典式攻击*程序，它循环访问所有字典 （或多个不同的语言字典） 中的单词并测试是否有任何单词就是用户的密码。 例如"美国"或"Mustang"弱密码可能被猜出快速。 更强的密码，如"？在L1N3vaFiNdMeyeP@sSWerd！"，是不大可能被猜出。 受密码保护的系统应确保用户选择强密码。  
  
 强密码是复杂 （包含大写、 小写字母、 数字和特殊字符的混合），并不是一个单词。 此示例演示如何验证复杂性。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 包含该密码的字符串表示通过调用此方法。  
  
 此示例需要：  
  
-   对 <xref:System.Text.RegularExpressions> 命名空间成员的访问权限。 如果未在代码中完全限定成员名称，则添加 `Imports` 语句。 有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="security"></a>安全性  
 如果你正在通过网络迁移密码，需要使用安全的方法来传输数据。 有关详细信息，请参阅[ASP.NET Web 应用程序安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))。
  
 您可以提高准确性`ValidatePassword`通过添加其他复杂性检查函数：  
  
-   将密码和针对用户的名称、 用户标识符和应用程序定义的字典及其子字符串进行比较。 执行比较时，将看上去很相似字符视为等效。 例如，将字母"l"和"e"视为等效于数字"1"和"3"。  
  
-   如果只有一个大写字符，请确保它不是密码的第一个字符。  
  
-   请确保密码的最后两个字符的字母字符。  
  
-   不允许从键盘的首行输入所有符号的密码。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Text.RegularExpressions.Regex>
- [ASP.NET Web 应用程序安全性](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))
