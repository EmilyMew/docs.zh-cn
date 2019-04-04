---
title: 在 Visual Basic 中实现 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 5fc96e1ae3624adc197b5b13029498b9aa90c95e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819497"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>演练：在 Visual Basic 中实现 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601>接口由类实现，可以一次返回一系列值的一项。 返回的数据一次的一项是不需要完整的数据集加载到内存中才能使用它的优点。 只需使用足够的内存将数据从加载单个项。 类实现`IEnumerable(T)`接口可与`For Each`循环或 LINQ 查询。  
  
 例如，假设应用程序必须读取一个大型文本文件，并从与特定搜索条件匹配的文件返回每个行。 应用程序使用 LINQ 查询返回与指定的条件匹配的文件中的行。 若要使用 LINQ 查询来查询该文件的内容，应用程序可以加载到一个数组或集合的文件的内容。 但是，将整个文件加载到数组或集合会占用比所需内存比以往更多的内存。 LINQ 查询无法使用 enumerable 类，返回与搜索条件匹配的值改为查询文件内容。 返回只有少量的查询匹配的值会占用更少内存。  
  
 可以创建一个实现类<xref:System.Collections.Generic.IEnumerable%601>接口，以公开可枚举的数据的源数据。 类实现`IEnumerable(T)`接口需要实现的另一个类<xref:System.Collections.Generic.IEnumerator%601>接口以循环访问源数据。 这两个类，可按顺序为特定类型返回的数据的项。  
  
 在本演练中，您将创建一个类实现`IEnumerable(Of String)`接口和类，用以实现`IEnumerator(Of String)`接口一次读取一行文本文件。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>创建可枚举类  
  
**创建可枚举类项目**

1.  在 Visual Basic 中上**文件**菜单，依次指向**新建**，然后单击**项目**。

1.  在“新建项目”对话框的“项目类型”窗格中，确保选中“Windows”。 在“模板”窗格中，选择“类库”。 在“名称”框中，键入 `StreamReaderEnumerable`，然后单击“确定”。 显示新的项目。

1.  在中**解决方案资源管理器**，右键单击 Class1.vb 文件，然后单击**重命名**。 将文件重命名为 `StreamReaderEnumerable.vb`，然后按 Enter。 重命名文件也会将类重命名为 `StreamReaderEnumerable`。 此类将实现 `IEnumerable(Of String)` 接口。

1.  右键单击 StreamReaderEnumerable 项目，指向**外**，然后单击**新项**。 选择**类**模板。 在中**名称**框中，键入`StreamReaderEnumerator.vb`然后单击**确定**。

 此项目中的第一个类是可枚举类，将实现`IEnumerable(Of String)`接口。 此泛型接口实现<xref:System.Collections.IEnumerable>接口，并保证此类的使用者可以访问值类型化为`String`。  
  
**添加代码以实现 IEnumerable**

1. 打开 StreamReaderEnumerable.vb 文件。

2. 在后面的行上`Public Class StreamReaderEnumerable`，键入以下命令并按 ENTER。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic 会自动填充具有所需的成员的类`IEnumerable(Of String)`接口。
  
3. 一次，此可枚举类将从一行文本文件读取行。 以下代码添加到类，以公开以文件路径作为输入参数的公共构造函数。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 实现<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法`IEnumerable(Of String)`接口将返回的新实例`StreamReaderEnumerator`类。 实现`GetEnumerator`方法`IEnumerable`接口可以成为`Private`，这是因为您必须将仅的成员公开`IEnumerable(Of String)`接口。 为 Visual Basic 生成的代码替换为`GetEnumerator`用下面的代码的方法。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**添加代码以实现 IEnumerator**

1. 打开 StreamReaderEnumerator.vb 文件。

2. 在后面的行上`Public Class StreamReaderEnumerator`，键入以下命令并按 ENTER。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic 会自动填充具有所需的成员的类`IEnumerator(Of String)`接口。

3. 枚举器类打开文本文件，并执行文件 I/O，以从文件读取的行。 以下代码添加到类，以公开以文件路径作为输入参数的公共构造函数并打开文本文件进行读取。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`属性都`IEnumerator(Of String)`并`IEnumerator`从文本文件作为接口返回的当前项`String`。 实现`Current`的属性`IEnumerator`接口可以成为`Private`，这是因为您必须将仅的成员公开`IEnumerator(Of String)`接口。 为 Visual Basic 生成的代码替换为`Current`属性使用以下代码。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`方法`IEnumerator`界面导航到文本文件中的下一项，并更新返回的值`Current`属性。 若要读取，没有其他项是否`MoveNext`方法将返回`False`; 否则为`MoveNext`方法将返回`True`。 将以下代码添加到 `MoveNext` 方法中。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`方法的`IEnumerator`接口指示迭代器指向文本文件的起点，并清除当前项的值。 将以下代码添加到 `Reset` 方法中。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`方法的`IEnumerator`接口可保证在销毁迭代器之前，释放所有非托管的资源。 使用的文件句柄`StreamReader`对象是一种非托管的资源和销毁该迭代器实例之前，必须关闭。 为 Visual Basic 生成的代码替换为`Dispose`用下面的代码的方法。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>使用示例迭代器

 可以在需要实现的对象的控制结构以及代码中使用 enumerable 类`IEnumerable`，如`For Next`循环或 LINQ 查询。 下面的示例演示`StreamReaderEnumerable`LINQ 查询中。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next 语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
