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
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="7cbcb-102">如何：读取图像元数据</span><span class="sxs-lookup"><span data-stu-id="7cbcb-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="7cbcb-103">某些图像文件包含元数据，您可以读取这些元数据来确定图像的功能。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="7cbcb-104">例如，数字照片可能包含元数据，您可以读取这些元数据来确定用于捕获图像的相机的品牌和型号。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="7cbcb-105">利用 GDI +，可以读取现有的元数据，还可以将新的元数据写入到图像文件。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="7cbcb-106">GDI + 将单独的元数据存储在 <xref:System.Drawing.Imaging.PropertyItem> 对象中。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="7cbcb-107">您可以读取 <xref:System.Drawing.Image.PropertyItems%2A> 对象的属性 <xref:System.Drawing.Image> ，以从文件中检索所有元数据。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="7cbcb-108"><xref:System.Drawing.Image.PropertyItems%2A>属性返回对象的数组 <xref:System.Drawing.Imaging.PropertyItem> 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="7cbcb-109"><xref:System.Drawing.Imaging.PropertyItem>对象具有以下四个属性： `Id` 、 `Value` 、 `Len` 和 `Type` 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="7cbcb-110">Id</span><span class="sxs-lookup"><span data-stu-id="7cbcb-110">Id</span></span>

<span data-ttu-id="7cbcb-111">标识元数据项的标记。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="7cbcb-112">下表显示了可以分配给的一些值 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> ：</span><span class="sxs-lookup"><span data-stu-id="7cbcb-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="7cbcb-113">十六进制值</span><span class="sxs-lookup"><span data-stu-id="7cbcb-113">Hexadecimal value</span></span>|<span data-ttu-id="7cbcb-114">说明</span><span class="sxs-lookup"><span data-stu-id="7cbcb-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="7cbcb-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="7cbcb-115">0x0320</span></span><br /><br /> <span data-ttu-id="7cbcb-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="7cbcb-116">0x010F</span></span><br /><br /> <span data-ttu-id="7cbcb-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="7cbcb-117">0x0110</span></span><br /><br /> <span data-ttu-id="7cbcb-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="7cbcb-118">0x9003</span></span><br /><br /> <span data-ttu-id="7cbcb-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="7cbcb-119">0x829A</span></span><br /><br /> <span data-ttu-id="7cbcb-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="7cbcb-120">0x5090</span></span><br /><br /> <span data-ttu-id="7cbcb-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="7cbcb-121">0x5091</span></span>|<span data-ttu-id="7cbcb-122">图像标题</span><span class="sxs-lookup"><span data-stu-id="7cbcb-122">Image title</span></span><br /><br /> <span data-ttu-id="7cbcb-123">设备制造商</span><span class="sxs-lookup"><span data-stu-id="7cbcb-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="7cbcb-124">设备型号</span><span class="sxs-lookup"><span data-stu-id="7cbcb-124">Equipment model</span></span><br /><br /> <span data-ttu-id="7cbcb-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="7cbcb-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="7cbcb-126">Exif 曝光时间</span><span class="sxs-lookup"><span data-stu-id="7cbcb-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="7cbcb-127">亮度表</span><span class="sxs-lookup"><span data-stu-id="7cbcb-127">Luminance table</span></span><br /><br /> <span data-ttu-id="7cbcb-128">色度表</span><span class="sxs-lookup"><span data-stu-id="7cbcb-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="7cbcb-129">值</span><span class="sxs-lookup"><span data-stu-id="7cbcb-129">Value</span></span>

<span data-ttu-id="7cbcb-130">一个 值数组。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-130">An array of values.</span></span> <span data-ttu-id="7cbcb-131">值的格式由 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 属性确定。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="7cbcb-132">Len</span><span class="sxs-lookup"><span data-stu-id="7cbcb-132">Len</span></span>

<span data-ttu-id="7cbcb-133">属性所指向的值数组的长度 (以字节为单位) <xref:System.Drawing.Imaging.PropertyItem.Value%2A> 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="7cbcb-134">类型</span><span class="sxs-lookup"><span data-stu-id="7cbcb-134">Type</span></span>

<span data-ttu-id="7cbcb-135">属性所指向的数组中的值的数据类型 `Value` 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="7cbcb-136">`Type`下表显示了属性值指示的格式：</span><span class="sxs-lookup"><span data-stu-id="7cbcb-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="7cbcb-137">数值</span><span class="sxs-lookup"><span data-stu-id="7cbcb-137">Numeric value</span></span>|<span data-ttu-id="7cbcb-138">说明</span><span class="sxs-lookup"><span data-stu-id="7cbcb-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="7cbcb-139">1</span><span class="sxs-lookup"><span data-stu-id="7cbcb-139">1</span></span>|<span data-ttu-id="7cbcb-140">一个 `Byte`</span><span class="sxs-lookup"><span data-stu-id="7cbcb-140">A `Byte`</span></span>|
|<span data-ttu-id="7cbcb-141">2</span><span class="sxs-lookup"><span data-stu-id="7cbcb-141">2</span></span>|<span data-ttu-id="7cbcb-142">`Byte`编码为 ASCII 的对象数组</span><span class="sxs-lookup"><span data-stu-id="7cbcb-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="7cbcb-143">3</span><span class="sxs-lookup"><span data-stu-id="7cbcb-143">3</span></span>|<span data-ttu-id="7cbcb-144">16位整数</span><span class="sxs-lookup"><span data-stu-id="7cbcb-144">A 16-bit integer</span></span>|
|<span data-ttu-id="7cbcb-145">4</span><span class="sxs-lookup"><span data-stu-id="7cbcb-145">4</span></span>|<span data-ttu-id="7cbcb-146">32位整数</span><span class="sxs-lookup"><span data-stu-id="7cbcb-146">A 32-bit integer</span></span>|
|<span data-ttu-id="7cbcb-147">5</span><span class="sxs-lookup"><span data-stu-id="7cbcb-147">5</span></span>|<span data-ttu-id="7cbcb-148">表示有理数的两个对象组成的数组 `Byte`</span><span class="sxs-lookup"><span data-stu-id="7cbcb-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="7cbcb-149">6</span><span class="sxs-lookup"><span data-stu-id="7cbcb-149">6</span></span>|<span data-ttu-id="7cbcb-150">未使用</span><span class="sxs-lookup"><span data-stu-id="7cbcb-150">Not used</span></span>|
|<span data-ttu-id="7cbcb-151">7</span><span class="sxs-lookup"><span data-stu-id="7cbcb-151">7</span></span>|<span data-ttu-id="7cbcb-152">未定义</span><span class="sxs-lookup"><span data-stu-id="7cbcb-152">Undefined</span></span>|
|<span data-ttu-id="7cbcb-153">8</span><span class="sxs-lookup"><span data-stu-id="7cbcb-153">8</span></span>|<span data-ttu-id="7cbcb-154">未使用</span><span class="sxs-lookup"><span data-stu-id="7cbcb-154">Not used</span></span>|
|<span data-ttu-id="7cbcb-155">9</span><span class="sxs-lookup"><span data-stu-id="7cbcb-155">9</span></span>|`SLong`|
|<span data-ttu-id="7cbcb-156">10</span><span class="sxs-lookup"><span data-stu-id="7cbcb-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="7cbcb-157">示例</span><span class="sxs-lookup"><span data-stu-id="7cbcb-157">Example</span></span>
  
<span data-ttu-id="7cbcb-158">下面的代码示例读取并显示文件中的七个元数据部分 `FakePhoto.jpg` 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="7cbcb-159">列表中的第二个 (index 1) 属性项具有 <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (设备制造商) 和 <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII 编码字节数组) 。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="7cbcb-160">此代码示例显示该属性项的值。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="7cbcb-161">此代码生成类似于以下内容的输出：</span><span class="sxs-lookup"><span data-stu-id="7cbcb-161">The code produces output similar to the following:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="7cbcb-162">编译代码</span><span class="sxs-lookup"><span data-stu-id="7cbcb-162">Compiling the Code</span></span>

<span data-ttu-id="7cbcb-163">前面的示例旨在与 Windows 窗体一起使用，并且它需要作为 <xref:System.Windows.Forms.PaintEventArgs> `e` <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="7cbcb-164">处理窗体的 <xref:System.Windows.Forms.Control.Paint> 事件，并将此代码粘贴到画图事件处理程序中。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="7cbcb-165">必须将替换 `FakePhoto.jpg` 为在系统中有效的映像名称和路径，然后导入该 `System.Drawing.Imaging` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="7cbcb-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cbcb-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cbcb-166">See also</span></span>

- [<span data-ttu-id="7cbcb-167">图像、位图和图元文件</span><span class="sxs-lookup"><span data-stu-id="7cbcb-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="7cbcb-168">使用图像、位图、图标和图元文件</span><span class="sxs-lookup"><span data-stu-id="7cbcb-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
