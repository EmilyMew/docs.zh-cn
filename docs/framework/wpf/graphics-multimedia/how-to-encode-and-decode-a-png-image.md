---
title: 如何：编码和解码 PNG 图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
ms.openlocfilehash: 46d4a7ffbfe7a6a620c26447cce30f3a0bd35adc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090844"
---
# <a name="how-to-encode-and-decode-a-png-image"></a>如何：编码和解码 PNG 图像
以下示例演示如何解码和编码[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]映像使用特定于<xref:System.Windows.Media.Imaging.PngBitmapDecoder>和<xref:System.Windows.Media.Imaging.PngBitmapEncoder>对象。  
  
## <a name="example"></a>示例  
 此示例演示如何进行解码[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]映像使用<xref:System.Windows.Media.Imaging.PngBitmapDecoder>从<xref:System.IO.FileStream>。  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a>示例  
 此示例演示如何进行编码<xref:System.Windows.Media.Imaging.BitmapSource>成[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]图像使用<xref:System.Windows.Media.Imaging.PngBitmapEncoder>。  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>请参阅

- [图像处理概述](imaging-overview.md)
