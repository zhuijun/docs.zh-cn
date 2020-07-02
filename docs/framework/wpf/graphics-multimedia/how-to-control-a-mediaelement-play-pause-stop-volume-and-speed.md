---
title: 如何：控制 MediaElement（播放、暂停、停止、音量和速度）
description: 控制 Windows Presentation foundation （WPF）中媒体的播放。 启动、停止、暂停、跳过和调整音量和速度。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853602"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="66a02-104">如何：控制 MediaElement（播放、暂停、停止、音量和速度）</span><span class="sxs-lookup"><span data-stu-id="66a02-104">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="66a02-105">下面的示例演示如何使用控制媒体的播放 <xref:System.Windows.Controls.MediaElement> 。</span><span class="sxs-lookup"><span data-stu-id="66a02-105">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="66a02-106">该示例创建了一个简单的 media player，使你可以在媒体中播放、暂停、停止和向后跳过，以及调整音量和速度比。</span><span class="sxs-lookup"><span data-stu-id="66a02-106">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a02-107">示例</span><span class="sxs-lookup"><span data-stu-id="66a02-107">Example</span></span>  
 <span data-ttu-id="66a02-108">下面的代码创建 UI。</span><span class="sxs-lookup"><span data-stu-id="66a02-108">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66a02-109"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>的属性 <xref:System.Windows.Controls.MediaElement> 必须设置为，以便 `Manual` 能够以交互方式停止、暂停和播放媒体。</span><span class="sxs-lookup"><span data-stu-id="66a02-109">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="66a02-110">示例</span><span class="sxs-lookup"><span data-stu-id="66a02-110">Example</span></span>  
 <span data-ttu-id="66a02-111">下面的代码实现了示例 UI 控件的功能。</span><span class="sxs-lookup"><span data-stu-id="66a02-111">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="66a02-112"><xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A> 方法用于分别播放、暂停和停止媒体。</span><span class="sxs-lookup"><span data-stu-id="66a02-112">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="66a02-113">通过更改 <xref:System.Windows.Controls.MediaElement.Position%2A> 的属性， <xref:System.Windows.Controls.MediaElement> 可以在媒体中跳过。</span><span class="sxs-lookup"><span data-stu-id="66a02-113">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="66a02-114">最后， <xref:System.Windows.Controls.MediaElement.Volume%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 属性用于调整媒体的音量和播放速度。</span><span class="sxs-lookup"><span data-stu-id="66a02-114">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="66a02-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66a02-115">See also</span></span>

- [<span data-ttu-id="66a02-116">使用情节提要控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="66a02-116">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
