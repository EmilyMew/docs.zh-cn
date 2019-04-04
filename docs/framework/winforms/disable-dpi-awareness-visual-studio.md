---
title: 禁用 Visual Studio 中的 DPI 识别功能
description: 讨论 HDPI 监视器上的 Windows 窗体设计器以及如何运行 Visual Studio 作为不识别 DPI 的进程的限制。
ms.date: 03/19/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 73f2371c40facf8902958cce020a6f02047615ba
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633863"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>禁用 Visual Studio 中的 DPI 识别功能

Visual Studio 是以每英寸点数 (DPI) 识别应用程序，这意味着会自动显示刻度。 如果应用程序指出它没有感知 DPI，操作系统将缩放应用程序作为位图。 此行为也被称为 DPI 虚拟化。 应用程序仍然认为它正以 100%缩放或 96 dpi。

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPI 监视器上的 Windows 窗体设计器

**Windows 窗体设计器**Visual Studio 中不具有缩放支持。 这会导致显示问题时打开中的某些窗体**Windows 窗体设计器**上高点 / 英寸 (HDPI) 监视器。 有关示例，可以显示控件重叠，如下图中所示：

![HDPI 监视器上的 Windows 窗体设计器](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

当你打开中的窗体**Windows 窗体设计器**HDPI 监视器上的 Visual Studio，在 Visual Studio 将在设计器顶部显示黄色条信息性：

![在不识别 DPI 的模式下重新启动 Visual Studio 中的信息栏](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

消息读取**主显示器上的缩放设置为 200%(192 dpi)。这可能导致设计器窗口中的呈现问题。**

> [!NOTE]
> 在 Visual Studio 2017 版本 15.8 引入了此信息栏。

如果您不能在设计器中工作并不需要调整窗体布局，可以忽略信息栏，并在代码编辑器中或在其他类型的设计器中继续工作。 (还可以[禁用通知](#disable-notifications)，以便不会继续显示信息栏。)仅**Windows 窗体设计器**受到影响。 如果需要在中工作**Windows 窗体设计器**下, 一步部分可帮助您[解决该问题](#to-resolve-the-problem)。

## <a name="to-resolve-the-problem"></a>若要解决此问题

有三个选项，若要解决显示问题的原因。

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>不识别 DPI 的过程中重新启动 Visual Studio

您可以重新启动 Visual Studio 作为不识别 DPI 的进程通过选择黄色信息栏上的选项。 这是解决此问题的首选的方法。

Visual Studio 运行时作为不识别 DPI 的进程，设计器布局问题已得到解决，但字体可能显示模糊。 Visual Studio 作为说不识别 DPI 的进程运行时将显示不同的黄色条信息性消息**作为不识别 DPI 的进程运行 Visual Studio。WPF 和 XAML 设计器可能无法正常显示。** 信息栏还提供了一个选项**作为 DPI 感知进程重新启动 Visual Studio**。

> [!NOTE]
> - 如果选择不识别 DPI 的过程中重新启动的选项时，必须取消停靠在 Visual Studio 中的工具窗口，可能会更改这些工具窗口的位置。
> - 如果使用默认的 Visual Basic 配置文件，或者你有**保存新项目时创建**中取消选择选项**工具** > **选项** > **项目和解决方案**，作为不识别 DPI 的进程重新启动时，Visual Studio 无法重新打开你的项目。 但是，可以通过选择下打开该项目**文件** > **最近使用的项目和解决方案**。

务必要完成其中的工作作为 DPI 感知进程重新启动 Visual Studio **Windows 窗体设计器**。 它作为运行时不识别 DPI 的过程，字体可以看起来很模糊和你可能会看到其他设计器中的问题，如**XAML 设计器**。 如果关闭并重新打开 Visual Studio，在不识别 DPI 的模式下运行时，它将成为 DPI 感知试。 此外可以单击**作为 DPI 感知进程重新启动 Visual Studio**信息栏中的选项。

### <a name="add-a-registry-entry"></a>添加一个注册表项

通过修改注册表，你可以将 Visual Studio 标记为 DPI 感知。 打开**注册表编辑器**并添加到一个条目**通过 NT\CurrentVersion\AppCompatFlags\Layers**子项：

**条目**:具体取决于是否使用 Visual Studio 2017 或 2019年，使用以下值之一：

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> 如果您使用的 Visual Studio Professional 或 Enterprise edition，替换**社区**与**Professional**或**企业**条目中。 此外将根据需要驱动器号。

**类型**:REG_SZ

**值**：DPIUNAWARE

> [!NOTE]
> Visual Studio 仍保持不识别 DPI 的模式，直到删除注册表项。

### <a name="set-your-display-scaling-setting-to-100"></a>将缩放到 100%的设置显示设置

若要设置您的显示设置为 100%缩放 Windows 10 中，键入**显示设置**在搜索框中，然后选择任务栏**更改显示设置**。 在中**设置**窗口中，将**更改的文本、 应用和其他项大小**到**100%**。

缩放到 100%将显示设置可能不希望如此，因为这可以使用户界面太小，才能使用。

## <a name="disable-notifications"></a>禁用通知

您可以选择不通知的 DPI 缩放在 Visual Studio 中的问题。 你可能想要禁用通知，如果您未使用在设计器中，例如。

若要禁用通知，请选择**工具** > **选项**以打开**选项**对话框。 然后，选择**Windows 窗体设计器** > **常规**，并设置**DPI 缩放通知**到**False**。

![DPI 缩放在 Visual Studio 中的通知选项](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

如果你想要以后重新启用缩放通知，将属性设置为 **，则返回 True**。

## <a name="troubleshoot"></a>疑难解答

如果 Visual Studio 中的预期，DPI 识别转换不起作用，检查以查看是否有`dpiAwareness`中的值**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image 文件执行 Options\devenv.exe**子项在注册表编辑器中。 如果存在，请删除值。

## <a name="see-also"></a>请参阅

- [Windows 窗体中的自动缩放](automatic-scaling-in-windows-forms.md)
