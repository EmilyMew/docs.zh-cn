---
title: 常量和枚举 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 0a9c01269e12c2d84be4f30c236c439012a88153
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839582"
---
# <a name="constants-and-enumerations-visual-basic"></a>常量和枚举 (Visual Basic)
Visual Basic 提供预定义的常量并为开发人员的枚举的数。 常量存储中保持不变的应用程序执行中的值。 枚举提供了使用相关常量集以及将常量值与名称相关联的一个便捷方法。  
  
## <a name="constants"></a>常量  
  
### <a name="conditional-compilation-constants"></a>条件编译常量  
 下表列出了可用于条件编译的预定义的常量。  
  
|**常量**|**说明**|  
|---|---|  
|`CONFIG`|与当前设置相对应的字符串**活动解决方案配置**框中**Configuration Manager**。|  
|`DEBUG`|一个`Boolean`值，可以在中设置该值**项目属性**对话框。 默认情况下，定义一个项目的调试配置`DEBUG`。 当`DEBUG`定义，则<xref:System.Diagnostics.Debug>类方法生成的输出**输出**窗口。 如果它不定义，<xref:System.Diagnostics.Debug>类方法不进行编译，不生成任何调试输出。|  
|`TARGET`|一个表示命令行中的设置或项目的输出类型的字符串 **/target**选项。 可能值`TARGET`是：<br /><br /> -"winexe"为 Windows 应用程序。<br />-"exe"的控制台应用程序。<br />-类库"库"。<br />-对于模块"模块"。<br />- **/Target**可能会在 Visual Studio 集成的开发环境中设置选项。 有关详细信息，请参阅[/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)。|  
|`TRACE`|一个`Boolean`值，可以在中设置该值**项目属性**对话框。 默认情况下，项目的所有配置都定义`TRACE`。 当`TRACE`定义，则<xref:System.Diagnostics.Trace>类方法生成的输出**输出**窗口。 未定义，当<xref:System.Diagnostics.Trace>类方法将不被编译，但不`Trace`生成输出。|  
|`VBC_VER`|一个表示 Visual Basic 版本中的数字*主要*。*次要*格式。 版本的版本号[!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]是 8.0。|  
  
### <a name="print-and-display-constants"></a>打印和显示常量  
 当调用打印和显示功能时，您可以代替实际值在代码中使用以下常量。  
  
|**常量**|**说明**|  
|---|---|  
|`vbCrLf`|回车/换行字符组合。|  
|`vbCr`|回车符。|  
|`vbLf`|换行字符。|  
|`vbNewLine`|换行字符。|  
|`vbNullChar`|Null 字符。|  
|`vbNullString`|与零长度字符串 ("");用于调用外部过程。|  
|`vbObjectError`|错误号。 用户定义的错误号应当大于此值。 例如：<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|字符的选项卡。|  
|`vbBack`|退格符。|  
|`vbFormFeed`|在 Microsoft Windows 中不使用。|  
|`vbVerticalTab`|不在 Microsoft Windows 中有用。|  
  
## <a name="enumerations"></a>枚举  
 下表列出并描述提供的 Visual Basic 的枚举。  
  
|枚举|描述|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|指示要为所调用的程序在调用时使用的窗口样式<xref:Microsoft.VisualBasic.Interaction.Shell%2A>函数。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|指示如何在调用音频方法时播放声音。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|指示角色检查调用时的类型<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>方法。|  
|<xref:Microsoft.VisualBasic.CallType>|指示在调用时要调用的过程类型<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>函数。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|指示如何比较字符串时调用比较函数。|  
|<xref:Microsoft.VisualBasic.DateFormat>|指示如何显示日期时调用<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>函数。|  
|<xref:Microsoft.VisualBasic.DateInterval>|指示当调用与日期相关的函数时如何确定日期间隔并设置其格式。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|指定要删除的目录包含文件或目录时应采取的操作。|  
|<xref:Microsoft.VisualBasic.DueDate>|指示时付款何时到期调用财务方法时。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|指示文本字段分隔的还是固定宽度。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|指示要调用文件访问函数时使用的文件属性。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|指示在调用与日期相关的函数时使用的每周的第一天。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|指示要在调用与日期相关的函数时使用的年份的第一周。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指示在消息框上按下了哪个按钮，由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数返回。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|指示调用 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数时显示的按钮。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|指示如何调用文件访问函数时打开的文件。|  
|<xref:Microsoft.VisualBasic.OpenMode>|指示如何调用文件访问函数时打开的文件。|  
|<xref:Microsoft.VisualBasic.OpenShare>|指示如何调用文件访问函数时打开的文件。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|指定一个文件是应永久删除还是放入回收站。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|指定是否以搜索所有或仅顶级目录。|  
|<xref:Microsoft.VisualBasic.TriState>|指示`Boolean`值或在调用数字格式设置函数时是否应使用默认值。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定应该是什么如果用户单击这样做**取消**一次操作中。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|指定复制、 删除或移动文件或目录时显示进度对话框。|  
|<xref:Microsoft.VisualBasic.VariantType>|指示变量对象，返回的类型<xref:Microsoft.VisualBasic.Information.VarType%2A>函数。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|指示调用 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函数时要执行的转换类型。|  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 语言参考](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [常量概述](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [枚举概述](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
