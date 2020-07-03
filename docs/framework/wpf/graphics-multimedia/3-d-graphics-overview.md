---
title: 三维图形概述
description: 熟悉 Windows Presentation Foundation （WPF）中的3D 图形，以便在标记和过程代码中绘制、转换和动画三维图形。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 51da6a1ed6d5e98b99c64ee23be52f7b2385897f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853872"
---
# <a name="3d-graphics-overview"></a>三维图形概述
<a name="introduction"></a>利用中的3D 功能， [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 开发人员可以在标记和过程代码中绘制、转换和动画三维图形。 开发人员可以结合2D 和3D 图形来创建丰富的控件、提供复杂的数据图，或增强应用程序界面的用户体验。 中的三维支持 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不是为提供功能齐全的游戏开发平台而设计的。 本主题概述了图形系统中的3D 功能 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2D 容器中的三维  
 中的3D 图形内容 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封装在一个元素中， <xref:System.Windows.Controls.Viewport3D> 该元素可以参与二维元素结构。 图形系统将 <xref:System.Windows.Controls.Viewport3D> 作为二维视觉元素，像中的许多其他元素一样 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 <xref:System.Windows.Controls.Viewport3D>作为一个窗口（视区）为一个三维场景。 更准确地说，它是一个在其上投影三维场景的图面。  
  
 在传统的2D 应用程序中，可以像使用 <xref:System.Windows.Controls.Viewport3D> 网格或画布这样的其他容器元素一样使用。  虽然您可以 <xref:System.Windows.Controls.Viewport3D> 在同一个场景图中使用与其他2d 绘图对象，但您不能渗透中的2d 和3d 对象 <xref:System.Windows.Controls.Viewport3D> 。  本主题将重点介绍如何在中绘制3D 图形 <xref:System.Windows.Controls.Viewport3D> 。  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>三维坐标空间  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]2d 图形的坐标系将原点定位在呈现区域（通常是屏幕）的左上角。 在二维系统中，正 x 轴值向右移动，正值 y 轴值向下移动。  但是，在3D 坐标系中，原点位于呈现区域的中心，正 x 轴值前进到右侧，而 y 轴上的正值朝上向右，而从原点向外前进到查看器。  
  
 ![坐标系统](./media/coordsystem-1.png "CoordSystem-1")  
传统的2D 和3D 坐标系统表示形式  
  
 这些轴定义的空间是中三维对象的固定参考框架 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 当在该空间中生成模型并创建光源和照相机以查看这些模型时，一定要在向每个模型应用转换时，将固定参考框架或“全局空间”与为该模型创建的局部参考框架区分开。 另请记住，根据光源和照相机设置，全局空间中的对象可能会看上去完全不同或者根本不可见，但是照相机的位置不会改变对象在全局空间中的位置。  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>照相机和投影  
 使用2D 的开发人员习惯于将绘图基元定位在二维屏幕上。 创建三维场景时，务必记住，确实要创建3D 对象的2D 表示形式。 由于三维场景看上去不同，具体取决于旁观者视角的观点，你必须指定该点。 <xref:System.Windows.Media.Media3D.Camera>类允许您为三维场景指定此视图点。  
  
 了解3D 场景如何在二维图面上表示的另一种方法是将场景描述为查看图面上的投影。 <xref:System.Windows.Media.Media3D.ProjectionCamera>允许您指定不同的投影及其属性，以更改旁观者视角查看3d 模型的方式。 <xref:System.Windows.Media.Media3D.PerspectiveCamera>指定 foreshortens 场景的投影。  换句话说， <xref:System.Windows.Media.Media3D.PerspectiveCamera> 提供消失点透视。  可以指定照相机在场景坐标系中的位置、照相机的方向和视野以及用来定义场景中“向上”方向的矢量。 下图说明了的 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 投影。  
  
 的 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 和 <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 属性 <xref:System.Windows.Media.Media3D.ProjectionCamera> 限制了照相机投影范围。 由于照相机可以位于场景中的任何位置，因此照相机实际上可能会位于模型内部或者紧靠模型，这使正确区分对象变得很困难。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>允许您指定与相机之间的最小距离，超过此值后将不会绘制对象。  相反， <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 使您可以指定与相机之间的距离，超过此距离将不会绘制对象，从而确保太远的对象不能被识别。  
  
 ![照相机设置](./media/coordsystem-6.png "CoordSystem-6")  
照相机位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>指定3D 模型到二维可视图面的正交投影。 与其他照相机一样，它指定位置、观察方向和“向上”方向。 但与不同的 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 是，描述不包含透视收缩的投影。 换句话说，描述了 <xref:System.Windows.Media.Media3D.OrthographicCamera> 一个边并行的查看框，而不是其边在相机中的某个点的位置。 下图显示了使用和查看的相同模型 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 。  
  
 ![正投影和透视投影](./media/camera-projections4.png "Camera_projections4")  
透视投影和正投影  
  
 下面的代码演示一些典型的照相机设置。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>模型和网格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D>表示泛型三维对象的抽象基类。 若要生成三维场景，需要查看一些对象，而组成场景图形的对象将派生自 <xref:System.Windows.Media.Media3D.Model3D> 。 目前， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支持对几何图形进行建模 <xref:System.Windows.Media.Media3D.GeometryModel3D> 。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>此模型的属性采用网状基元。  
  
 若要生成模型，请首先生成一个基元或网格。 3D 基元是单个 3D 实体中的顶点的集合。 大多数三维系统提供了在最简单闭合图形上建模的基元：由三个顶点定义的三角形。  由于三角形的三个点在一个平面上，因此可以继续添加三角形，以便对网格这样较为复杂的形状建模。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 系统当前提供 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 类，这允许您指定任何几何图形; 它目前不支持预定义的3d 基元（如球体和立方形式）。 开始创建， <xref:System.Windows.Media.Media3D.MeshGeometry3D> 方法是将三角形顶点的列表指定为其 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 属性。 每个顶点都指定为 <xref:System.Windows.Media.Media3D.Point3D> 。  （在中 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，将此属性指定为在死去中分组的编号列表，表示每个顶点的坐标。）根据其几何图形，网格可能由多个三角形组成，其中一些三角形共享相同的角（顶点）。 若要正确绘制网格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要有关哪些顶点由哪些三角形共用的信息。 您可以通过使用属性指定三角形索引的列表来提供此信息 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 。 此列表指定列表中指定的点 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 将确定三角形的顺序。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在前面的示例中， <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 列表指定8个顶点来定义多维数据集网格。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>属性指定包含三个索引的十二个组的列表。  列表中的每个数字都是指列表的偏移量 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。  例如，列表指定的前三个顶点 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 为（1，1，0）、（0，1，0）和（0，0，0）。 列表指定的前三个索引 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 为0、2和1，它们对应于列表中的第一个、第三个和第二个点 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。 因此，构成立方体模型的第一个三角形将按照从 (1,1,0) 到 (0,1,0) 再到 (0,0,0) 的顺序组合而成，其余的十一个三角形将按照类似方式确定。  
  
 您可以通过指定和属性的值继续定义模型 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 。  为了呈现模型的图面，图形系统需要有关曲面在任何给定三角形上的朝向信息。 图形系统使用此信息来针对该模型进行照明计算：正对光源的图面比偏离光源的图面显得更亮。 尽管 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置坐标来确定默认的法矢量，但是你还可以指定不同的法矢量来近似计算曲面的外观。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>属性指定一个集合 <xref:System.Windows.Point> ，该集合告诉图形系统如何映射确定如何绘制纹理到网格顶点的坐标。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>指定为0和1之间的值（包括0和1）。  与属性一样 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> ，图形系统可以计算默认纹理坐标，但您可以选择设置不同的纹理坐标来控制包含重复模式部分的纹理的映射，例如。 有关纹理坐标的详细信息，可在后续主题或 Managed Direct3D SDK 中找到。  
  
 下面的示例演示如何在过程代码中创建立方体模型的一面。 可以将整个多维数据集绘制为单个 GeometryModel3D;此示例将多维数据集的人脸绘制为不同的模型，以便以后将单独的纹理应用于每个面。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>向模型应用材料  
  
 为了使网格看上去像三维对象，必须向其应用纹理，以便覆盖由顶点和三角形定义的图面，从而使其可以由照相机照明和投影。 在2D 中，使用 <xref:System.Windows.Media.Brush> 类将颜色、图案、渐变或其他视觉对象应用到屏幕区域。  不过，3D 对象的外观是照明模型的一种功能，而不只是应用于它们的颜色或图案。 实际对象的图面质量不同，它们反射光的方式也会有所不同：光亮的图面与粗糙或不光滑的图面看上去不同，某些对象似乎可以吸收光，而某些对象似乎能够发光。 您可以将所有相同的画笔应用于可应用于2D 对象的3D 对象，但不能直接应用它们。  
  
 若要定义模型的图面特征，请 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 <xref:System.Windows.Media.Media3D.Material> 抽象类。 Material 的具体子类用来确定模型图面的某些外观特征，每个子类还提供一个可以向其传递 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 属性。  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>指定将画笔应用于模型，就好像该模型是漫射的。 使用 DiffuseMaterial 与在二维模型上直接使用画笔最相似;模型图面不会像发光一样反射光。  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>指定将画笔应用于模型，就像模型的图面为 "硬" 或 "光亮"，可以反射高光。 您可以通过为属性指定一个值来设置纹理向其推荐此反射质量的程度或 "闪光" <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> 。  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>允许您指定将应用纹理，就好像模型发射的光线等于画笔的颜色一样。 这不会使模型成为光源；但是它参与阴影设置的方式将不同于用 DiffuseMaterial 或 SpecularMaterial 设置纹理时的情况。  
  
 为了获得更好的性能，backfaces 是 <xref:System.Windows.Media.Media3D.GeometryModel3D> 从场景中剔除的（因为它们在模型中相对于照相机的另一侧）。  若要指定 <xref:System.Windows.Media.Media3D.Material> 要应用于模型的隐（如平面）的，请设置模型的 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> 属性。  
  
 为了实现某些图面质量（如发光或发射效果），用户可能希望向模型连续应用几个不同的画笔。 您可以使用类来应用和重复使用多个材料 <xref:System.Windows.Media.Media3D.MaterialGroup> 。 MaterialGroup 的子级在多个呈现过程中按照从头到尾的顺序来应用。  
  
 下面的代码示例演示如何将纯色和绘图作为画笔应用于三维模型。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>照亮场景  
 三维图形中的灯光在现实世界中有什么光源：它们会使表面可见。 更确切地说，光确定了场景的哪个部分将包括在投影中。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光对象创建了各种光和阴影效果，并且按照各种实际光的行为进行了建模。 在场景中包含至少一个光源，否则不会显示任何模型。  
  
 以下灯光派生自基类 <xref:System.Windows.Media.Media3D.Light> ：  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>：提供各种环境照明，无论其位置或方向如何，都将统一照亮所有对象。  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>：类似于远处的光源。  定向光源的 <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> 指定为 Vector3D，但未指定位置。  
  
- <xref:System.Windows.Media.Media3D.PointLight>：类似于附近的光源。 PointLights 具有一个位置并从该位置投射光。 场景中的对象根据对象相对于光源的位置和距离被照亮。 <xref:System.Windows.Media.Media3D.PointLightBase>公开一个 <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> 属性，该属性确定不会通过光来确定模型的距离。 System.windows.media.media3d.pointlight> 还公开了衰减属性，这些属性确定光线强度如何随距离减弱。 可以为光源的衰减指定恒定、线性或二次内插算法。  
  
- <xref:System.Windows.Media.Media3D.SpotLight>：从继承 <xref:System.Windows.Media.Media3D.PointLight> 。 Spotlights 的照亮方式与 PointLight 类似，但是它既具有位置又具有方向。 它们按 <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> 和 <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> 属性（以度为单位）指定的锥形区域中的项目光线。  
  
 光源是 <xref:System.Windows.Media.Media3D.Model3D> 对象，因此可以转换和动画光属性，其中包括位置、颜色、方向和范围。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>转换模型  
 创建模型时，它们在场景中有特定的位置。 为了在场景中移动、旋转这些模型或者更改这些模型的大小而更改用来定义模型本身的顶点不切实际。  与在2D 中一样，可以将转换应用于模型。  
  
 每个模型对象都有一个 <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> 属性，您可以使用该属性对模型进行移动、重定向或调整大小。  应用转换时，实际上是按照由转换功能指定的矢量或值（以适用者为准）来偏移模型的所有点。 换言之，用户已经转换了在其中定义模型的坐标空间（“模型空间”），但是尚未更改在整个场景的坐标系（“全局空间”）中构成模型几何形状的值。  
  
 有关转换模型的详细信息，请参阅[三维转换概述](3-d-transformations-overview.md)。  
  
<a name="animations"></a>
## <a name="animating-models"></a>对模型进行动画处理  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 实现与2d 图形参与相同的计时和动画系统。 换句话说，若要对三维场景进行动画处理，请对其模型的属性进行动画处理。 可以直接对基元的属性进行动画处理，但是通常很容易对用来更改模型位置或外观的转换进行动画处理。 由于转换可以应用于 <xref:System.Windows.Media.Media3D.Model3DGroup> 对象以及单个模型，因此，可以将一组动画应用到 Model3DGroup 的子级，并将另一组动画应用于一组子对象。 还可以通过对场景的照明属性进行动画处理来实现各种视觉效果。 最后，可以选择通过对照相机的位置或视野进行动画处理来对投影本身进行动画处理。 有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 计时和动画系统的背景信息，请参阅[动画概述](animation-overview.md)、[演示图板概述](storyboards-overview.md)和 [Freezable 对象概述](../advanced/freezable-objects-overview.md)主题。  
  
 若要对 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的对象进行动画处理，可以创建时间线、定义动画（实际上是随着时间的推移而更改某个属性值）并指定要向其应用动画的属性。 由于三维场景中的所有对象都是的子级 <xref:System.Windows.Controls.Viewport3D> ，因此要应用于场景的任何动画的目标属性都是 Viewport3D 的属性。  
  
 假设你希望实现模型看上去是在原地摇摆的效果。 您可以选择将应用 <xref:System.Windows.Media.Media3D.RotateTransform3D> 到模型，并将其从一个向量旋转到另一个向量的轴进行动画处理。 下面的代码示例演示如何将 Vector3DAnimation 应用于该转换的 Rotation3D 的 Axis 属性，并假设 RotateTransform3D 是应用于具有 TransformGroup 的模型的几个转换之一。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>向窗口添加3D 内容  
 若要呈现场景，请将模型和灯光添加到 <xref:System.Windows.Media.Media3D.Model3DGroup> ，然后将设置 <xref:System.Windows.Media.Media3D.Model3DGroup> 为 <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> 的 <xref:System.Windows.Media.Media3D.ModelVisual3D> 。 将添加 <xref:System.Windows.Media.Media3D.ModelVisual3D> 到 <xref:System.Windows.Controls.Viewport3D.Children%2A> 的集合 <xref:System.Windows.Controls.Viewport3D> 。 通过设置照相机的属性，将其添加到中 <xref:System.Windows.Controls.Viewport3D> <xref:System.Windows.Controls.Viewport3D.Camera%2A> 。  
  
 最后，将添加 <xref:System.Windows.Controls.Viewport3D> 到窗口中。 如果 <xref:System.Windows.Controls.Viewport3D> 包含为与画布类似的布局元素的内容，请通过设置其 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 属性（继承自）来指定 Viewport3D 的大小 <xref:System.Windows.FrameworkElement> 。  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [三维转换概述](3-d-transformations-overview.md)
- [最大程度地提高 WPF 三维性能](maximize-wpf-3d-performance.md)
- [操作指南主题](3-d-graphics-how-to-topics.md)
- [WPF 中的形状和基本图形概述](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用图像、图形和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
