---
title: 位图类型
description: 了解位图类型和支持的 GDI + 图形文件格式，包括 BMP、JPG、GIF、PNG 和 TIFF。
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
ms.openlocfilehash: 09b74ef476467b0bba5aac1f58db278b3898ef17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174674"
---
# <a name="types-of-bitmaps"></a>位图类型
位图是指定像素的矩形数组中每个像素的颜色的位数组。 专用于单个像素的位数决定了可以分配给该像素的颜色数。 例如，如果每个像素由4位表示，则给定的像素可以分配16种不同的颜色 (2 ^ 4 = 16) 。 下表显示了几个示例，其中显示了可以分配给给定位数表示的像素的颜色数。  
  
|每像素位数|可分配给像素的颜色数|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 存储位图的磁盘文件通常包含存储信息的一个或多个信息块，如每个像素的位数、每行中的像素数以及数组中的行数。 此类文件可能还包含颜色表 (有时称为调色板) 。 颜色表将位图中的数字映射到特定的颜色。 下图显示了一个放大的图像及其位图和颜色表。 每个像素由一个4位数字表示，因此颜色表中有 2 ^ 4 = 16 种颜色。 表中的每种颜色都由一个24位数字表示：8位表示红色，8位表示绿色，8位表示蓝色。 数字以十六进制 (以16为基数) 形式显示： A = 10、B = 11、C = 12、D = 13、E = 14、F = 15。  
  
 ![位图示例](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 查看图像第3行第5列的像素。 位图中的相应数字是1。 颜色表告诉我们，1表示红色，因此像素为红色。 位图顶部行中的所有项都是3。 颜色表告诉我们，3表示蓝色，因此图像的首行中的所有像素都是蓝色的。  
  
> [!NOTE]
> 某些位图以自下而上的格式存储;位图第一行中的数字对应于图像底部行中的像素。  
  
 将索引存储到颜色表的位图称为调色板索引的位图。 某些位图无需使用颜色表。 例如，如果位图使用每个像素24位，则位图可以存储颜色本身，而不是将索引存储到颜色表中。 下图显示了一个位图，该位图将颜色直接存储 (每像素24位) 而不是使用颜色表。 该图还显示了相应图像的放大视图。 在位图中，FFFFFF 表示白色，FF0000 表示红色，00FF00 表示绿色，0000FF> 表示蓝色。  
  
 ![位图示例](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>图形文件格式  
 有许多标准格式可用于将位图保存到磁盘文件中。 GDI + 支持以下各段中所述的图形文件格式。  
  
### <a name="bmp"></a>BMP  
 BMP 是 Windows 用于存储与设备无关的和与应用程序无关的映像的一种标准格式。 给定 BMP 文件的每个像素的位数 (1、4、8、15、24、32或 64) 在文件头中指定。 每像素24位的 BMP 文件很常见。 BMP 文件通常不会进行压缩，因此不适合在 Internet 上传输。  
  
### <a name="graphics-interchange-format-gif"></a>图形交换格式 (GIF)  
 GIF 是在网页上显示的图像的常用格式。 Gif 可以很好地用于线条绘图、包含纯色块的图片以及颜色之间具有清晰边界的图片。 Gif 已压缩，但压缩过程中不会丢失任何信息;解压缩的映像与原始映像完全相同。 可以将 GIF 中的一种颜色指定为透明，使图像具有显示该图像的任何网页的背景色。 GIF 图像的序列可以存储在单个文件中，以形成动态 GIF。 Gif 存储最多每像素8位，因此它们的颜色限制为256。  
  
### <a name="joint-photographic-experts-group-jpeg"></a>联合图像专家组 (JPEG)  
 JPEG 是一种适用于自然场景的压缩方案，如扫描的照片。 在压缩过程中，某些信息会丢失，但让的情况通常会丢失。 Jpeg 存储每像素24位，因此它们能够显示16000000以上的颜色。 Jpeg 不支持透明或动画。  
  
 JPEG 图像中的压缩级别是可配置的，但较高的压缩级别 (较小的文件) 会导致更多的信息丢失。 20:1 的压缩率通常会生成一个图像，该图像会使人眼发现难以区分原始图像。 下图显示了一个 BMP 图像和两个从 BMP 图像压缩的 JPEG 图像。 第一个 JPEG 的压缩率为4:1，第二个 jpeg 的压缩率为约8:1。  
  
 ![Filetype 示例](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG 压缩不适用于线条绘图、纯色块和锐边界。 下图显示了一个 BMP 以及两个 Jpeg 和 GIF。 Jpeg 和 GIF 是从 BMP 压缩而来的。 对于 GIF，压缩率为4:1，对于较小的 JPEG 则为4:1，对于较大的 JPEG 则为8:3。 请注意，GIF 沿直线保持锐边界，但 Jpeg 往往会使边界模糊。  
  
 ![Filetype](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG 是压缩方案，而不是文件格式。 JPEG 文件交换格式 (JFIF) 是通常用于存储和传输已根据 JPEG 方案进行压缩的图像的文件格式。 Web 浏览器显示的 JFIF 文件使用 .jpg 扩展名。  
  
### <a name="exchangeable-image-file-exif"></a>可交换图像文件 (EXIF)   
 EXIF 是一种用于数码相机捕获照片的文件格式。 EXIF 文件包含根据 JPEG 规范进行压缩的映像。 EXIF 文件还包含有关照片的信息 (拍摄日期、快门速度、曝光时间等) 以及有关相机 (制造商、型号等) 的信息。  
  
### <a name="portable-network-graphics-png"></a>可移植网络图形 (PNG)  
 PNG 格式保留了 GIF 格式的许多优点，但也提供了除 GIF 以外的功能。 与 GIF 文件一样，PNG 文件在压缩后不会丢失信息。 PNG 文件可存储具有8、24或48位/像素的颜色，以及每个像素1、2、4、8或16位的灰度。 与此相反，GIF 文件只能使用1、2、4或8位/像素。 PNG 文件还可以存储每个像素的 alpha 值，指定该像素的颜色与背景色混合的程度。  
  
 PNG 在 GIF 中的改进功能可以逐渐显示图像 (也就是说，在通过网络连接) 时，可更好、更好地将图像更近似地显示。 PNG 文件可以包含伽玛更正和颜色更正信息，以便能够在各种显示设备上准确呈现图像。  
  
### <a name="tag-image-file-format-tiff"></a>标记图像文件格式 (TIFF)   
 TIFF 是一种灵活且可扩展的格式，由各种平台和图像处理应用程序支持。 TIFF 文件可以存储具有任意数量的每像素位数的图像，并可以使用多种压缩算法。 多个图像可以存储在一个多页 TIFF 文件中。 与映像相关的信息 (扫描程序、主机计算机、压缩类型、方向、每个像素的样本等等，) 可以存储在文件中，并通过使用标记进行排列。 TIFF 格式可以根据需要通过审批和添加新标记进行扩展。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
