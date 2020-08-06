---
title: 如何使用平台调用播放 WAV 文件 - C# 编程指南
description: 此 C# 代码示例说明了如何使用平台调用服务在 Windows 操作系统中播放 WAV 声音文件。
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: b30cb08e2dcde0eb85e8d88a690ae24bf7ae7f22
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302979"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="c87dc-103">如何使用平台调用播放 WAV 文件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="c87dc-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="c87dc-104">下面的 C# 代码示例说明了如何使用平台调用服务在 Windows 操作系统中播放 WAV 声音文件。</span><span class="sxs-lookup"><span data-stu-id="c87dc-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="c87dc-105">示例</span><span class="sxs-lookup"><span data-stu-id="c87dc-105">Example</span></span>

<span data-ttu-id="c87dc-106">此示例代码使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 将 `winmm.dll` 的 `PlaySound` 方法入口点导入为 `Form1 PlaySound()`。</span><span class="sxs-lookup"><span data-stu-id="c87dc-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="c87dc-107">本示例具有一个带按钮的简单 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="c87dc-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="c87dc-108">单击该按钮将打开一个标准的 Windows <xref:System.Windows.Forms.OpenFileDialog> 对话框，以便你可以打开要播放的文件。</span><span class="sxs-lookup"><span data-stu-id="c87dc-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="c87dc-109">选中波形文件后，该文件将使用 winmm.dll 库的 `PlaySound()` 方法播放。</span><span class="sxs-lookup"><span data-stu-id="c87dc-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="c87dc-110">有关此方法的详细信息，请参阅[使用 PlaySound 功能处理波形音频文件](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files)。</span><span class="sxs-lookup"><span data-stu-id="c87dc-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="c87dc-111">浏览并选择具有 .wav 扩展名的文件，然后单击“打开”以使用平台调用播放波形文件。</span><span class="sxs-lookup"><span data-stu-id="c87dc-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="c87dc-112">文本框中显示所选文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="c87dc-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="c87dc-113">通过筛选器设置对“打开文件”对话框进行筛选，以仅显示扩展名为 .wav 的文件：</span><span class="sxs-lookup"><span data-stu-id="c87dc-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="c87dc-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="c87dc-114">Compiling the code</span></span>

1. <span data-ttu-id="c87dc-115">在 Visual Studio 中创建一个新的 C# Windows Forms 应用程序项目，并将其命名为“WinSound”。</span><span class="sxs-lookup"><span data-stu-id="c87dc-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="c87dc-116">复制上面的代码，将其粘贴到 Form1.cs 文件的内容中。</span><span class="sxs-lookup"><span data-stu-id="c87dc-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="c87dc-117">复制以下代码，然后将其粘贴到 `InitializeComponent()` 方法中 Form1.Designer.cs 文件的任何现有代码之后。</span><span class="sxs-lookup"><span data-stu-id="c87dc-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="c87dc-118">编译并运行该代码。</span><span class="sxs-lookup"><span data-stu-id="c87dc-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c87dc-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c87dc-119">See also</span></span>

- [<span data-ttu-id="c87dc-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c87dc-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c87dc-121">互操作性概述</span><span class="sxs-lookup"><span data-stu-id="c87dc-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="c87dc-122">平台调用详解</span><span class="sxs-lookup"><span data-stu-id="c87dc-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="c87dc-123">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="c87dc-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
