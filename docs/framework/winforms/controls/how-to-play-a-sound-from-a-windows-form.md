---
title: 如何：从 Windows 窗体播放声音
description: 了解如何在运行时从给定路径的 Windows 窗体播放声音。 另外，了解如何编译代码和 .NET 安全框架。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613743"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>如何：从 Windows 窗体播放声音
本示例在运行时播放给定路径中的声音。

## <a name="example"></a>示例

```vb
Sub PlaySimpleSound()
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")
End Sub
```

```csharp
private void playSimpleSound()
{
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");
    simpleSound.Play();
}
```

## <a name="compiling-the-code"></a>编译代码
 此示例需要：

- 即，使用有效的文件名替换文件名 `"c:\Windows\Media\chimes.wav"`。

- 导向命名空间的引用 <xref:System.Media?displayProperty=nameWithType> 。

## <a name="robust-programming"></a>可靠编程
 文件操作应包含在相应的结构化异常处理块内。

 以下情况可能会导致异常：

- 路径名称格式不正确。 例如，它包含非法字符或它仅为空格（<xref:System.ArgumentException> 类）。

- 此路径为只读路径（<xref:System.IO.IOException> 类）。

- 此路径名为 `null`（<xref:System.ArgumentNullException> 类）。

- 此路径名过长（<xref:System.IO.PathTooLongException> 类）。

- 路径无效（<xref:System.IO.DirectoryNotFoundException> 类）。

- 路径仅为冒号 "：" （ <xref:System.NotSupportedException> 类）。

## <a name="net-framework-security"></a>.NET Framework 安全性
 不要根据文件的名称来判断文件的内容。 例如，文件 `Form1.vb` 可能不是 Visual Basic 源文件。 在应用程序中使用输入的数据之前，需验证所有的输入内容。

## <a name="see-also"></a>请参阅

- <xref:System.Media.SoundPlayer>
- [如何：在 Windows 窗体内异步加载声音](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
