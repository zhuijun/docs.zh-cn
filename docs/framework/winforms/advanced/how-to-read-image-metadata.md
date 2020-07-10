---
title: 如何：读取图像元数据
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174661"
---
# <a name="how-to-read-image-metadata"></a>如何：读取图像元数据

某些图像文件包含元数据，您可以读取这些元数据来确定图像的功能。 例如，数字照片可能包含元数据，您可以读取这些元数据来确定用于捕获图像的相机的品牌和型号。 利用 GDI +，可以读取现有的元数据，还可以将新的元数据写入到图像文件。

GDI + 将单独的元数据存储在 <xref:System.Drawing.Imaging.PropertyItem> 对象中。 您可以读取 <xref:System.Drawing.Image.PropertyItems%2A> 对象的属性 <xref:System.Drawing.Image> ，以从文件中检索所有元数据。 <xref:System.Drawing.Image.PropertyItems%2A>属性返回对象的数组 <xref:System.Drawing.Imaging.PropertyItem> 。

<xref:System.Drawing.Imaging.PropertyItem>对象具有以下四个属性： `Id` 、 `Value` 、 `Len` 和 `Type` 。

## <a name="id"></a>Id

标识元数据项的标记。 下表显示了可以分配给的一些值 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> ：

|十六进制值|说明|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|图像标题<br /><br /> 设备制造商<br /><br /> 设备型号<br /><br /> ExifDTOriginal<br /><br /> Exif 曝光时间<br /><br /> 亮度表<br /><br /> 色度表|

## <a name="value"></a>值

一个 值数组。 值的格式由 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 属性确定。

## <a name="len"></a>Len

属性所指向的值数组的长度 (以字节为单位) <xref:System.Drawing.Imaging.PropertyItem.Value%2A> 。

## <a name="type"></a>类型

属性所指向的数组中的值的数据类型 `Value` 。 `Type`下表显示了属性值指示的格式：

|数值|说明|
|-------------------|-----------------|
|1|一个 `Byte`|
|2|`Byte`编码为 ASCII 的对象数组|
|3|16位整数|
|4|32位整数|
|5|表示有理数的两个对象组成的数组 `Byte`|
|6|未使用|
|7|未定义|
|8|未使用|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>示例
  
下面的代码示例读取并显示文件中的七个元数据部分 `FakePhoto.jpg` 。 列表中的第二个 (index 1) 属性项具有 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (设备制造商) 和 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII 编码字节数组) 。 此代码示例显示该属性项的值。

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

此代码生成类似于以下内容的输出：

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a>编译代码

前面的示例旨在与 Windows 窗体一起使用，并且它需要作为 <xref:System.Windows.Forms.PaintEventArgs> `e` <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。 处理窗体的 <xref:System.Windows.Forms.Control.Paint> 事件，并将此代码粘贴到画图事件处理程序中。 必须将替换 `FakePhoto.jpg` 为在系统中有效的映像名称和路径，然后导入该 `System.Drawing.Imaging` 命名空间。

## <a name="see-also"></a>另请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
