---
title: Option Infer 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: a3846c952969a4814151757c5210d9df6f3c97b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823488"
---
# <a name="option-infer-statement"></a>Option Infer 语句
允许声明变量时使用局部类型推理。  
  
## <a name="syntax"></a>语法  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`On`|可选。 启用局部类型推理。|  
|`Off`|可选。 禁用局部类型推理。|  
  
## <a name="remarks"></a>备注  
 若要在文件中设置 `Option Infer`，请在任何其他源代码之前、文件顶部键入 `Option Infer On` 或 `Option Infer Off`。 如果为文件中 `Option Infer` 设置的值与在 IDE 中或在命令行上设置的值冲突，则文件中的值优先。  
  
 将 `Option Infer` 设置为 `On`时，你可以无需显式声明数据类型就声明本地变量。 编译器会从其初始化表达式的类型推断出变量的数据类型。  
  
 在下图中，`Option Infer` 处于打开状态。 声明 `Dim someVar = 2` 中的变量由类型推理声明为整数。

 下面的屏幕截图显示了 IntelliSense，Option Infer 处于打开时： 
  
 ![Option Infer 处于上时显示 IntelliSense 视图的屏幕截图。](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 在下图中，`Option Infer` 处于关闭状态。 声明 `Dim someVar = 2` 中的变量由类型推理声明为 `Object`。 在此示例中， **Option Strict**设置为**Off**上[编译页，项目设计器 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
 Option Infer 处于关闭状态时，以下屏幕截图显示了 IntelliSense:
 
 ![Option Infer 处于关闭状态时显示 IntelliSense 视图的屏幕截图。](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  变量声明为 `Object` 时，可在程序运行时更改运行时类型。 Visual Basic 执行调用的操作*装箱*并*取消装箱*之间进行转换`Object`和值类型，这会使执行速度较慢。 有关装箱和取消装箱的信息，请参阅[Visual Basic 语言规范](~/_vblang/spec/conversions.md#value-type-conversions)。
  
 类型推理适用于过程级，且在类、结构、模块或接口中的过程之外不适用。  
  
 有关其他信息，请参阅[本地类型推断](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>当 Option Infer 语句不存在时  
 如果源代码不包含`Option Infer`语句中， **Option Infer**上设置[编译页，项目设计器 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)使用。 如果使用命令行编译器，则[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)使用编译器选项。  
  
#### <a name="to-set-option-infer-in-the-ide"></a>若要在 IDE 中设置 Option Infer  
  
1.  在“解决方案资源管理器”中，选择一个项目。 在“项目”菜单上，单击“属性”。  
  
2.  单击“编译”选项卡。  
  
3.  中的值设置**Option infer**框。  
  
 创建一个新项目时**Option Infer**上设置**编译**选项卡设置为**Option Infer**中设置**VB 默认值**对话框。 访问**VB 默认值**对话框中，在**工具**菜单中，单击**选项**。 在“选项”对话框中，展开“项目和解决方案”，然后单击“VB 默认值”。 中的初始默认设置**VB 默认值**是`On`。  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>若要设置命令行上的 Option Infer  
  
-   包括[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)中的编译器选项**vbc**命令。  
  
## <a name="default-data-types-and-values"></a>默认数据类型和值  
 下表描述了指定 `Dim` 语句中数据类型和初始值设定项的各种组合的结果。  
  
|是否指定数据类型？|是否指定初始值设定项？|示例|结果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 处于关闭状态（默认），则将变量设置为 `Nothing`。<br /><br /> 如果 `Option Strict` 处于打开状态，则发生编译时错误。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 处于打开状态（默认），则变量采用初始值设定项的数据类型。 请参阅[局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 和 `Option Strict` 均处于关闭状态，则变量采用 `Object` 的数据类型。<br /><br /> 如果 `Option Infer` 处于关闭状态但 `Option Strict` 处于打开状态，则发生编译时错误。|  
|是|否|`Dim qty As Integer`|将变量初始化为数据类型的默认值。 有关详细信息，请参阅[Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始值设定项的数据类型不可转换为指定数据类型，则会发生编译时错误。|  
  
## <a name="example"></a>示例  
 下例演示了 `Option Infer` 语句启用局部类型推理的方式。  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>示例  
 下例演示了变量被标识为 `Object` 时运行时类型可以改变的情况。  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>请参阅

- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [装箱和取消装箱](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
