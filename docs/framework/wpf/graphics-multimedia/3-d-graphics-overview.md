---
title: 三维图形概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 79dc7a3578c395ae8cdf5933e1249441f97071a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087984"
---
# <a name="3-d-graphics-overview"></a>三维图形概述
<a name="introduction"></a>通过 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 功能，开发人员可以使用标记和程序代码绘制和转换 3D 图形，并对其进行动画处理。 开发人员可以合并 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] 和 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 图形以创建丰富的控件、提供复杂的数据图解，或者增强用户对应用程序界面的体验。 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 支持在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]并非旨在提供一个全功能的游戏开发平台。 本主题概述了 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 图形系统中的 [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 功能。  

<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>2D 容器中的 3D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 图形中的内容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]封装在一个元素， <xref:System.Windows.Controls.Viewport3D>，该元素可以参与二维元素结构。 该图形系统将<xref:System.Windows.Controls.Viewport3D>等中的许多其他的二维视觉元素作为[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 <xref:System.Windows.Controls.Viewport3D> 为窗口函数，视区 — 到三维场景。 更准确地说，它是 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 场景所投影到的图面。  
  
 在传统[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]应用程序中，使用<xref:System.Windows.Controls.Viewport3D>就像 Grid 或 Canvas 之类的另一个容器元素。  尽管可以使用<xref:System.Windows.Controls.Viewport3D>与其他[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]对象绘制在同一个场景图中，您不能结合[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]并[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]中的对象<xref:System.Windows.Controls.Viewport3D>。  本主题将重点介绍如何绘制[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]内的图形<xref:System.Windows.Controls.Viewport3D>。  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3D 坐标空间  
 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 图形的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 坐标系将原点定位在呈现区域（通常是屏幕）的左上角。 在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 系统中，x 轴上的正值朝右，y 轴上的正值朝下。  但是，在 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 坐标系中，原点位于呈现区域的中心，x 轴上的正值朝右，但是 y 轴上的正值朝上，z 轴上的正值从原点向外朝向观察者。  
  
 ![坐标系](./media/coordsystem-1.png "CoordSystem 1")  
传统的 2D 和 3D 坐标系表示形式  
  
 由这些轴定义的空间是 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 对象在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的固定参考框架。 当在该空间中生成模型并创建光源和照相机以查看这些模型时，一定要在向每个模型应用转换时，将固定参考框架或“全局空间”与为该模型创建的局部参考框架区分开。 另请记住，根据光源和照相机设置，全局空间中的对象可能会看上去完全不同或者根本不可见，但是照相机的位置不会改变对象在全局空间中的位置。  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>照相机和投影  
 处理 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 的开发人员习惯于将绘图基元置于二维屏幕上。 创建 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 场景时，务必记住实际上是要创建 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 对象的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 表示形式。 由于 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 场景的外观会因观察者的观察位置而异，因此必须指定观察位置。 <xref:System.Windows.Media.Media3D.Camera>类，可指定这种观点的[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]场景。  
  
 了解 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 场景如何在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 图面上表示的另一种方法就是将场景描述为到观察表面上的投影。 <xref:System.Windows.Media.Media3D.ProjectionCamera>允许您指定不同的投影和其属性以更改观察者如何查看[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]模型。 一个<xref:System.Windows.Media.Media3D.PerspectiveCamera>指定 foreshortens 场景的投影。  换而言之，<xref:System.Windows.Media.Media3D.PerspectiveCamera>提供消失点透视。  可以指定照相机在场景坐标系中的位置、照相机的方向和视野以及用来定义场景中“向上”方向的矢量。 下图说明了<xref:System.Windows.Media.Media3D.PerspectiveCamera>的投影。  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>并<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>的属性<xref:System.Windows.Media.Media3D.ProjectionCamera>限制照相机的投影范围。 由于照相机可以位于场景中的任何位置，因此照相机实际上可能会位于模型内部或者紧靠模型，这使正确区分对象变得很困难。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 可以指定从照相机超过该值将不绘制对象的最小距离。  相反， <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> ，可以指定一个距离照相机超过该值将不绘制对象，这样可以确保对象太远而无法识别不会包括在场景。  
  
 ![照相机设置](./media/coordsystem-6.png "CoordSystem 6")  
照相机位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> 指定的正交投影[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]模型到[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]可视化图面。 与其他照相机一样，它指定位置、观察方向和“向上”方向。 与不同<xref:System.Windows.Media.Media3D.PerspectiveCamera>，但是，<xref:System.Windows.Media.Media3D.OrthographicCamera>描述不包括透视收缩的投影。 换而言之，<xref:System.Windows.Media.Media3D.OrthographicCamera>描述了一个边是并行的而不是一个其侧面汇集在照相机上的点。 下图显示了相同的模型，如使用查看<xref:System.Windows.Media.Media3D.PerspectiveCamera>和<xref:System.Windows.Media.Media3D.OrthographicCamera>。  
  
 ![正投影和透视投影](./media/camera-projections4.png "Camera_projections4")  
透视投影和正投影  
  
 下面的代码演示一些典型的照相机设置。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>模型和网格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D> 是表示泛型的抽象基类[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]对象。 若要构建[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]场景，需要某些对象，若要查看，并构成场景图对象派生自<xref:System.Windows.Media.Media3D.Model3D>。 目前，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支持使用几何形状进行建模<xref:System.Windows.Media.Media3D.GeometryModel3D>。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>此模型的属性采用网格基元。  
  
 若要生成模型，请首先生成一个基元或网格。 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 基元是一系列构成单个 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 实体的顶点。 大多数 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 系统都提供在最简单的闭合图（由三个顶点定义的三角形）上建模的基元。  由于三角形的三个点在一个平面上，因此可以继续添加三角形，以便对网格这样较为复杂的形状建模。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]系统目前提供<xref:System.Windows.Media.Media3D.MeshGeometry3D>类，可用于指定任何几何形状; 目前不支持预定义[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]基元，如球体和立方体。 开始创建<xref:System.Windows.Media.Media3D.MeshGeometry3D>通过指定为三角形顶点的列表及其<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>属性。 每个顶点都指定为<xref:System.Windows.Media.Media3D.Point3D>。  （在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，将该属性指定为三个一组的数字列表，每组中的三个数字表示每个顶点的坐标）。根据网格的几何形状，网格可能会由多个三角形组成，有些三角形共用相同的角（顶点）。 若要正确绘制网格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要有关哪些顶点由哪些三角形共用的信息。 通过指定的与的三角形索引列表提供此信息<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>属性。 此列表指定点在指定的顺序<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>列表将确定一个三角形。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在前面的示例中，<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>列表指定八个顶点来定义立方体形状的网格。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>属性指定由三个索引的十二个组的列表。  在列表中的每个数字的偏移量是指<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>列表。  例如，由指定的前三个顶点<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>列表是否 (1,1,0) (0,1,0) 和 (0,0,0)。 指定的前三个索引<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>列表是 0、 2 和 1，其中第三，对应于第一个和第二个中的点<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>列表。 因此，构成立方体模型的第一个三角形将按照从 (1,1,0) 到 (0,1,0) 再到 (0,0,0) 的顺序组合而成，其余的十一个三角形将按照类似方式确定。  
  
 您可以继续通过指定的值定义模型<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>和<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>属性。  为了呈现模型的图面，图形系统需要有关曲面在任何给定三角形上的朝向信息。 图形系统使用此信息来针对该模型进行照明计算：正对光源的图面比偏离光源的图面显得更亮。 尽管 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置坐标来确定默认的法矢量，但是你还可以指定不同的法矢量来近似计算曲面的外观。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>属性指定的集合<xref:System.Windows.Point>用于通知图形系统如何映射确定如何将纹理绘制到网格的顶点的坐标。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 被指定为 0 和 1 之间，非独占值。  与使用<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>属性，该图形系统可以计算默认纹理坐标，但是您可以选择设置不同的纹理坐标，例如包括重复图案一部分的纹理的映射进行控制。 有关纹理坐标的详细信息，可在后续主题或 Managed Direct3D SDK 中找到。  
  
 下面的示例演示如何在过程代码中创建立方体模型的一面。 请注意，可以将整个立方体绘制为单个 GeometryModel3D；此示例将该立方体面绘制为一个不同的模型，以便在以后向每个面应用不同的纹理。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>向模型应用材料  
  
 为了使网格看上去像三维对象，必须向其应用纹理，以便覆盖由顶点和三角形定义的图面，从而使其可以由照相机照明和投影。 在中[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]，则使用<xref:System.Windows.Media.Brush>类要应用于屏幕区域的颜色、 图案、 渐变或其他可视内容。  但是，[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 对象的外观是照明模型的功能，而不只是应用于它们的颜色或图案。 实际对象的图面质量不同，它们反射光的方式也会有所不同：光亮的图面与粗糙或不光滑的图面看上去不同，某些对象似乎可以吸收光，而某些对象似乎能够发光。 可以向 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 对象应用与应用于 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 对象的完全相同的画笔，但是不能直接应用它们。  
  
 定义特性的模型的图面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用<xref:System.Windows.Media.Media3D.Material>抽象类。 Material 的具体子类用来确定模型图面的某些外观特征，每个子类还提供一个可以向其传递 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 属性。  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> 指定将向模型应用画笔，就好像该模型已漫射光来照亮。 使用 DiffuseMaterial 与直接针对 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 模型使用画笔非常相似；模型表面不反射光，就好像是自发光一样。  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> 指定将向模型应用画笔，就像模型的表面坚硬或者光亮，能够反射高光。 可以通过指定的值设置到此反射特质或"，"建议纹理的程度<xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A>属性。  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> 可以指定将应用纹理，就好像模型所发出的光与画笔的颜色。 这不会使模型成为光源；但是它参与阴影设置的方式将不同于用 DiffuseMaterial 或 SpecularMaterial 设置纹理时的情况。  
  
 为了提高性能的背面<xref:System.Windows.Media.Media3D.GeometryModel3D>（有视图之外，因为它们是将模型从照相机在相反一侧这些人脸） 可以从场景。  若要指定<xref:System.Windows.Media.Media3D.Material>若要将应用于的模型如飞机隐面，将设置该模型的<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>属性。  
  
 为了实现某些图面质量（如发光或发射效果），用户可能希望向模型连续应用几个不同的画笔。 可以将应用并通过重用多个材料<xref:System.Windows.Media.Media3D.MaterialGroup>类。 MaterialGroup 的子级在多个呈现过程中按照从头到尾的顺序来应用。  
  
 下面的代码示例演示如何将纯色和绘图以画笔形式应用于 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 模型。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>照亮场景  
 与实际的光一样，[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 图形中的光能够使图面可见。 更确切地说，光确定了场景的哪个部分将包括在投影中。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光对象创建了各种光和阴影效果，并且按照各种实际光的行为进行了建模。 必须至少在场景中包括一个光，否则模型将不可见。  
  
 下面的光派生自的基类<xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>:提供环境照明照亮所有对象，其位置或方向无关。  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>:像远处的光源那样照亮。  具有方向性光源<xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A>指定为 Vector3D，但是没有指定的位置。  
  
-   <xref:System.Windows.Media.Media3D.PointLight>:像近处的光源那样照亮。 PointLights 具有一个位置并从该位置投射光。 场景中的对象根据对象相对于光源的位置和距离被照亮。 <xref:System.Windows.Media.Media3D.PointLightBase> 公开<xref:System.Windows.Media.Media3D.PointLightBase.Range%2A>属性，用于确定位置距离，超过该模型将不会由光源照亮。 PointLight 还公开了多个衰减属性，这些属性确定光源的亮度如何随距离的增加而减小。 可以为光源的衰减指定恒定、线性或二次内插算法。  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>:继承自 <xref:System.Windows.Media.Media3D.PointLight>。 Spotlights 的照亮方式与 PointLight 类似，但是它既具有位置又具有方向。 这些项目中设置的锥形区域的 light<xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A>和<xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A>以度为单位指定的属性。  
  
 光源是<xref:System.Windows.Media.Media3D.Model3D>对象，因此可以转换，并对光源属性，包括位置、 颜色、 方向和范围进行动画处理。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>转换模型  
 创建模型时，它们在场景中有特定的位置。 为了在场景中移动、旋转这些模型或者更改这些模型的大小而更改用来定义模型本身的顶点不切实际。  而正如在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 中一样，可以向模型应用转换。  
  
 每个模型对象具有<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>属性与其可以移动、 重定向或调整模型的大小。  应用转换时，实际上是按照由转换功能指定的矢量或值（以适用者为准）来偏移模型的所有点。 换言之，用户已经转换了在其中定义模型的坐标空间（“模型空间”），但是尚未更改在整个场景的坐标系（“全局空间”）中构成模型几何形状的值。  
  
 有关转换模型的详细信息，请参阅 [3D 转换概述](3-d-transformations-overview.md)。  
  
<a name="animations"></a>   
## <a name="animating-models"></a>对模型进行动画处理  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 实现与 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 图形参与同一个计时和动画系统。 换言之，若要对 3D 场景进行动画处理，需要对其模型的属性进行动画处理。 可以直接对基元的属性进行动画处理，但是通常很容易对用来更改模型位置或外观的转换进行动画处理。 由于转换可以应用于<xref:System.Windows.Media.Media3D.Model3DGroup>对象、 单个模型，可以将一组动画应用于向 Model3DGroup 的子级和另一组子对象的一组动画。 还可以通过对场景的照明属性进行动画处理来实现各种视觉效果。 最后，可以选择通过对照相机的位置或视野进行动画处理来对投影本身进行动画处理。 有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 计时和动画系统的背景信息，请参阅[动画概述](animation-overview.md)、[演示图板概述](storyboards-overview.md)和 [Freezable 对象概述](../advanced/freezable-objects-overview.md)主题。  
  
 若要对 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的对象进行动画处理，可以创建时间线、定义动画（实际上是随着时间的推移而更改某个属性值）并指定要向其应用动画的属性。 因为中的所有对象[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]场景是子级<xref:System.Windows.Controls.Viewport3D>，面向想要应用于场景的任何动画的属性是 Viewport3D 的属性的属性。  
  
 假设你希望实现模型看上去是在原地摇摆的效果。 可以选择要应用<xref:System.Windows.Media.Media3D.RotateTransform3D>到模型中，并从一个矢量旋转到另一个轴进行动画处理。 下面的代码示例演示如何将 Vector3DAnimation 应用于该转换的 Rotation3D 的 Axis 属性，并假设 RotateTransform3D 是应用于具有 TransformGroup 的模型的几个转换之一。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>向窗口中添加 3D 内容  
 若要呈现场景，将添加模型和到光源<xref:System.Windows.Media.Media3D.Model3DGroup>，然后设置<xref:System.Windows.Media.Media3D.Model3DGroup>作为<xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A>的<xref:System.Windows.Media.Media3D.ModelVisual3D>。 添加<xref:System.Windows.Media.Media3D.ModelVisual3D>到<xref:System.Windows.Controls.Viewport3D.Children%2A>的集合<xref:System.Windows.Controls.Viewport3D>。 添加到相机<xref:System.Windows.Controls.Viewport3D>通过设置其<xref:System.Windows.Controls.Viewport3D.Camera%2A>属性。  
  
 最后，添加<xref:System.Windows.Controls.Viewport3D>到窗口。 当<xref:System.Windows.Controls.Viewport3D>是包含作为画布，如布局元素的内容指定通过设置 Viewport3D 的大小及其<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>属性 (继承自<xref:System.Windows.FrameworkElement>)。  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [三维变换概述](3-d-transformations-overview.md)
- [最大程度地提高 WPF 三维性能](maximize-wpf-3d-performance.md)
- [帮助主题](3-d-graphics-how-to-topics.md)
- [WPF 中的形状和基本图形概述](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用图像、图形和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
