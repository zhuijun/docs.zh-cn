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
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="1ba0a-104">如何：从 Windows 窗体播放声音</span><span class="sxs-lookup"><span data-stu-id="1ba0a-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="1ba0a-105">本示例在运行时播放给定路径中的声音。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="1ba0a-106">示例</span><span class="sxs-lookup"><span data-stu-id="1ba0a-106">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="1ba0a-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="1ba0a-107">Compiling the Code</span></span>
 <span data-ttu-id="1ba0a-108">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="1ba0a-108">This example requires:</span></span>

- <span data-ttu-id="1ba0a-109">即，使用有效的文件名替换文件名 `"c:\Windows\Media\chimes.wav"`。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="1ba0a-110">导向命名空间的引用 <xref:System.Media?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="1ba0a-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="1ba0a-111">Robust Programming</span></span>
 <span data-ttu-id="1ba0a-112">文件操作应包含在相应的结构化异常处理块内。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="1ba0a-113">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="1ba0a-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="1ba0a-114">路径名称格式不正确。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-114">The path name is malformed.</span></span> <span data-ttu-id="1ba0a-115">例如，它包含非法字符或它仅为空格（<xref:System.ArgumentException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="1ba0a-116">此路径为只读路径（<xref:System.IO.IOException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="1ba0a-117">此路径名为 `null`（<xref:System.ArgumentNullException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="1ba0a-118">此路径名过长（<xref:System.IO.PathTooLongException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="1ba0a-119">路径无效（<xref:System.IO.DirectoryNotFoundException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="1ba0a-120">路径仅为冒号 "：" （ <xref:System.NotSupportedException> 类）。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="1ba0a-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1ba0a-121">.NET Framework Security</span></span>
 <span data-ttu-id="1ba0a-122">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="1ba0a-123">例如，文件 `Form1.vb` 可能不是 Visual Basic 源文件。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="1ba0a-124">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="1ba0a-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ba0a-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ba0a-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="1ba0a-126">如何：在 Windows 窗体内异步加载声音</span><span class="sxs-lookup"><span data-stu-id="1ba0a-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
