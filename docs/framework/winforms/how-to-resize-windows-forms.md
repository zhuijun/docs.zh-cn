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
# <a name="how-to-resize-windows-forms"></a>如何：调整 Windows 窗体的大小

可使用多种方式指定 Windows 窗体的大小。 可以通过设置 <xref:System.Windows.Forms.Form.Size%2A> 属性的新值，或单独调整 <xref:System.Windows.Forms.Control.Height%2A> 或 <xref:System.Windows.Forms.Control.Width%2A> 属性，以编程方式更改窗体的高度和宽度。 如果使用的是 Visual Studio，则可以使用 Windows 窗体设计器更改大小。 另请参阅[如何：使用设计器调整 Windows 窗体大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))。

## <a name="resize-a-form-programmatically"></a>以编程方式调整窗体的大小

在运行时通过设置窗体的 <xref:System.Windows.Forms.Form.Size%2A> 属性，定义窗体的大小。

以下代码示例显示窗体大小设置为 100 × 100 像素。

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>以编程方式更改窗体的宽度和高度

定义 <xref:System.Windows.Forms.Form.Size%2A> 后，通过使用 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 属性更改窗体的高度或宽度。

以下代码示例显示自窗体左边缘起，窗体宽度设置为 300 像素，而高度保持不变。

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

\- 或 -

通过设置 <xref:System.Windows.Forms.Form.Size%2A> 属性更改 <xref:System.Drawing.Size.Width%2A> 或 <xref:System.Drawing.Size.Height%2A>。

但是，如以下代码示例所示，这种方法比只设置 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 属性更繁琐。

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>以编程方式更改窗体大小

若要增加窗体大小，则设置 <xref:System.Drawing.Size.Width%2A> 和 <xref:System.Drawing.Size.Height%2A> 属性。

以下代码示例显示高于当前设置的 200 像素窗体宽度。

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
> 始终使用 <xref:System.Drawing.Size.Height%2A> 或 <xref:System.Drawing.Size.Width%2A> 属性更改窗体维度，除非正在通过将 <xref:System.Windows.Forms.Form.Size%2A> 属性设置为一个新 <xref:System.Drawing.Size> 结构来同时设置高度和宽度。 <xref:System.Windows.Forms.Form.Size%2A> 属性将返回 <xref:System.Drawing.Size> 结构，此结构是值类型。 不能将新值分配给值类型的属性。 例如，以下代码示例将不会编译。

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

## <a name="see-also"></a>另请参阅

- [入门与 Windows 窗体](getting-started-with-windows-forms.md)
- [增强 Windows 窗体应用程序](./advanced/index.md)
