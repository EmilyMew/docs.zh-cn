---
title: 位图类型
ms.date: 03/30/2017
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
ms.openlocfilehash: f41585ba8816e0b1894a9f01163191848ae391e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089152"
---
# <a name="types-of-bitmaps"></a>位图类型
位图的像素为单位的矩形数组中指定的每个像素的颜色的位数组。 专用于单个像素的比特数确定可以分配给该像素的颜色数。 例如，如果每个像素都由 4 位，则给定的像素可以指定 16 种不同颜色之一 (2 ^4 = 16)。 下表显示了几个示例的给定数目的位可以分配给代表的像素的颜色数。  
  
|每像素位数|可以分配给一个像素的颜色数|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 通常存储位图的磁盘文件包含一个或多个数组中存储每个像素，每个行中的像素数和行数的比特数等信息的信息块。 此类文件还可能包含颜色表 （有时称为调色板）。 颜色表映射到特定的颜色位图中的数字。 下图显示了放大的图像连同其位图和颜色的表。 每个像素都由一个 4 位数字，因此有 2 ^4 = 16 种颜色的颜色表中。 表中的每个颜色表示为一个 24 位数字：8 位用于表示红色、 绿色、 8 位和 8 位用于蓝色。 数字显示十六进制 (基数为 16) 窗体中：A = 10，B = 11，C = 12，D = 13，E = 14，F = 15。  
  
 ![位图示例](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 看看在第 3 行、 第 5 列图像的像素。 位图中的相应编号为 1。 颜色表告诉我们 1 表示红色，因此该像素是红色。 位图的顶行中的所有项都是 3。 颜色表告诉我们，3 表示蓝色，因此图像的顶部行中的所有像素都是蓝色。  
  
> [!NOTE]
>  某些位图存储在自下而上的格式;位图的第一行中的数字对应于像素的图像的底部行中。  
  
 将索引存储到颜色表的位图称为索引调色板的位图。 某些位图使用颜色表不需要。 例如，如果位图使用每像素 24 位，该位图可以存储颜色本身而不是索引颜色表。 下图显示位图，用于存储直接颜色 （24 位 / 像素），而不是使用颜色表。 该插图还显示相应的映像的放大的视图。 在位图中 FFFFFF 表示白色、 FF0000 表示红色、 00FF00 表示绿色，和 0000ff> 表示蓝色。  
  
 ![位图示例](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>图形文件格式  
 有许多标准格式的磁盘文件中保存位图。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支持的图形文件格式在以下各段中所述。  
  
### <a name="bmp"></a>BMP  
 BMP 是用于存储与设备无关且独立于应用程序的映像的 Windows 的标准格式。 文件头中指定每个像素 （1、 4、 8、 15、 24、 32 或 64） 对于给定的 BMP 文件的比特数。 使用每像素 24 位 BMP 文件很常见。 BMP 文件通常不压缩，因此，不是很适合用于传输在 Internet 上。  
  
### <a name="graphics-interchange-format-gif"></a>图形交换格式 (GIF)  
 GIF 是用于在网页显示的图像的通用格式。 Gif 图像适用于行绘图、 用纯色，块的图片和有颜色之间的清晰边界的图片。 Gif 图像被压缩，但压缩进程; 中丢失任何信息解压缩的映像完全是与原始对象相同。 Gif 文件中的一种颜色指定为透明的以便该图像将出现显示它的任何 Web 页面的背景色。 GIF 图像一系列可以存储在单个文件，以形成动态 gif 图。 Gif 图像存储最多 8 位 / 像素，因此它们限制为 256 种颜色。  
  
### <a name="joint-photographic-experts-group-jpeg"></a>联合图像专家组 (JPEG)  
 JPEG 是一种非常适用于扫描的照片如自然场景压缩方案。 在压缩过程中，会丢失一些信息，但通常丢失是察觉不到人眼。 Jpeg 存储 24 位 / 像素，因此它们能够显示超过 1600 万种颜色。 Jpeg 不支持透明度或动画。  
  
 JPEG 图像中的压缩级别可配置，但更高的压缩级别 （较小的文件） 会导致丢失更多的信息。 20:1 的压缩率通常生成人眼查找难以区分从原始的映像。 下图显示了 BMP 图像和从该 BMP 图像压缩的两个 JPEG 图像。 第一个 JPEG 压缩比率 4:1，第二个 JPEG 大约 8:1 的压缩比率。  
  
 ![Filetype 示例](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG 压缩不很适合线型的纯色，块和清晰边界。 下图显示了 BMP 以及两个 Jpeg 和为 gif 图像。 Jpeg 图像和 gif 图像被压缩从 BMP。 压缩率较小的 jpeg，和更大的 jpeg 8:3 是 GIF、 4:1 4:1。 请注意，GIF 维护清晰的边界，代码行，但往往会模糊边界 jpeg 图像。  
  
 ![Filetypes](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG 压缩方案，而不是文件格式。 JPEG 文件交换格式 (JFIF) 是常用于存储和传输 JPEG 方案根据已压缩的图像文件格式。 通过 Web 浏览器显示的 JFIF 文件使用.jpg 扩展名。  
  
### <a name="exchangeable-image-file-exif"></a>可交换图像文件 (EXIF)  
 EXIF 是用于通过数字相机捕获照片文件格式。 EXIF 文件包含压缩根据 JPEG 规范的图像。 EXIF 文件还包含有关照片的信息 （拍摄日期、 快门速度、 曝光时间等） 和照相机 （制造商、 型号和等等） 有关的信息。  
  
### <a name="portable-network-graphics-png"></a>可移植网络图形 (PNG)  
 PNG 格式保留许多 GIF 格式的优点，但还提供了功能超越 GIF。 GIF 文件，如 PNG 文件被压缩且不会丢失的信息。 PNG 文件可以存储与 8、 24 个，或 48 位 / 像素的灰度与 1、 2、 4、 8、 或每像素 16 位颜色。 与此相反，GIF 文件可以使用仅为 1、 2、 4 或 8 位 / 像素。 PNG 文件还可以存储指定该像素的颜色混合使用背景色的程度的每个像素的 alpha 值。  
  
 PNG 可改善的功能，以渐进方式显示的图像 GIF （也就是说，若要显示的图像的更好和更好的近似值为它到达时通过网络连接）。 PNG 文件可以包含伽玛校正和颜色更正信息，以便映像可以准确地呈现在各种显示设备上。  
  
### <a name="tag-image-file-format-tiff"></a>标记图像文件格式 (TIFF)  
 TIFF 是一种灵活且可扩展的格式，支持的各种平台和图像处理应用程序。 TIFF 文件可以存储具有任意数目的位 / 像素的图像，可以使用各种压缩算法。 多个映像可以存储在单一、 多页的 TIFF 文件。 与映像 （扫描仪制造商、 主机、 压缩、 方向、 每个像素和等等的示例类型的） 相关的信息可以存储在文件中并使用标签来排列。 根据需要通过审批并添加新标签，可以扩展 TIFF 格式。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
