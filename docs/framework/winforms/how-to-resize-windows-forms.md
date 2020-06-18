---
title: 调整窗体大小
description: 了解如何通过为 "Size" 属性设置新值或分别调整 "高度" 或 "宽度" 属性来调整窗体的高度和宽度。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 0d6383e4d29d9407d3da97bf8b94761f06d99748
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903267"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="40c57-103">如何：调整 Windows 窗体的大小</span><span class="sxs-lookup"><span data-stu-id="40c57-103">How to: Resize Windows Forms</span></span>

<span data-ttu-id="40c57-104">可使用多种方式指定 Windows 窗体的大小。</span><span class="sxs-lookup"><span data-stu-id="40c57-104">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="40c57-105">可以通过设置 <xref:System.Windows.Forms.Form.Size%2A> 属性的新值，或单独调整 <xref:System.Windows.Forms.Control.Height%2A> 或 <xref:System.Windows.Forms.Control.Width%2A> 属性，以编程方式更改窗体的高度和宽度。</span><span class="sxs-lookup"><span data-stu-id="40c57-105">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="40c57-106">如果使用的是 Visual Studio，则可以使用 Windows 窗体设计器更改大小。</span><span class="sxs-lookup"><span data-stu-id="40c57-106">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="40c57-107">另请参阅[如何：使用设计器调整 Windows 窗体大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="40c57-107">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="40c57-108">以编程方式调整窗体的大小</span><span class="sxs-lookup"><span data-stu-id="40c57-108">Resize a form programmatically</span></span>

<span data-ttu-id="40c57-109">在运行时通过设置窗体的 <xref:System.Windows.Forms.Form.Size%2A> 属性，定义窗体的大小。</span><span class="sxs-lookup"><span data-stu-id="40c57-109">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="40c57-110">以下代码示例显示窗体大小设置为 100 × 100 像素。</span><span class="sxs-lookup"><span data-stu-id="40c57-110">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="40c57-111">以编程方式更改窗体的宽度和高度</span><span class="sxs-lookup"><span data-stu-id="40c57-111">Change form width and height programmatically</span></span>

<span data-ttu-id="40c57-112">定义 <xref:System.Windows.Forms.Form.Size%2A> 后，通过使用 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 属性更改窗体的高度或宽度。</span><span class="sxs-lookup"><span data-stu-id="40c57-112">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="40c57-113">以下代码示例显示自窗体左边缘起，窗体宽度设置为 300 像素，而高度保持不变。</span><span class="sxs-lookup"><span data-stu-id="40c57-113">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="40c57-114">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="40c57-114">-or-</span></span>

<span data-ttu-id="40c57-115">通过设置 <xref:System.Windows.Forms.Form.Size%2A> 属性更改 <xref:System.Drawing.Size.Width%2A> 或 <xref:System.Drawing.Size.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="40c57-115">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="40c57-116">但是，如以下代码示例所示，这种方法比只设置 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 属性更繁琐。</span><span class="sxs-lookup"><span data-stu-id="40c57-116">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="40c57-117">以编程方式更改窗体大小</span><span class="sxs-lookup"><span data-stu-id="40c57-117">Change form size by increments programmatically</span></span>

<span data-ttu-id="40c57-118">若要增加窗体大小，则设置 <xref:System.Drawing.Size.Width%2A> 和 <xref:System.Drawing.Size.Height%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="40c57-118">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="40c57-119">以下代码示例显示高于当前设置的 200 像素窗体宽度。</span><span class="sxs-lookup"><span data-stu-id="40c57-119">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="40c57-120">始终使用 <xref:System.Drawing.Size.Height%2A> 或 <xref:System.Drawing.Size.Width%2A> 属性更改窗体维度，除非正在通过将 <xref:System.Windows.Forms.Form.Size%2A> 属性设置为一个新 <xref:System.Drawing.Size> 结构来同时设置高度和宽度。</span><span class="sxs-lookup"><span data-stu-id="40c57-120">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="40c57-121"><xref:System.Windows.Forms.Form.Size%2A> 属性将返回 <xref:System.Drawing.Size> 结构，此结构是值类型。</span><span class="sxs-lookup"><span data-stu-id="40c57-121">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="40c57-122">不能将新值分配给值类型的属性。</span><span class="sxs-lookup"><span data-stu-id="40c57-122">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="40c57-123">例如，以下代码示例将不会编译。</span><span class="sxs-lookup"><span data-stu-id="40c57-123">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="40c57-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40c57-124">See also</span></span>

- [<span data-ttu-id="40c57-125">入门与 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="40c57-125">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="40c57-126">增强 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="40c57-126">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
