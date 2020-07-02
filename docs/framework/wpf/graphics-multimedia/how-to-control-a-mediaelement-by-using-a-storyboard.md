---
title: 如何：使用演示图板控制 MediaElement
description: 使用 Windows Presentation foundation （WPF）中的情节提要控制媒体的播放。 请考虑此示例来创建简单的媒体播放器。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853735"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="99c25-104">如何：使用演示图板控制 MediaElement</span><span class="sxs-lookup"><span data-stu-id="99c25-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="99c25-105">此示例演示如何使用中的来控制 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 。</span><span class="sxs-lookup"><span data-stu-id="99c25-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c25-106">示例</span><span class="sxs-lookup"><span data-stu-id="99c25-106">Example</span></span>  
 <span data-ttu-id="99c25-107">当使用中的 <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 来控制的时间时 <xref:System.Windows.Controls.MediaElement> ，该功能与其他对象（如动画）的功能相同 <xref:System.Windows.Media.Animation.Timeline> 。</span><span class="sxs-lookup"><span data-stu-id="99c25-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="99c25-108">例如，使用属性 <xref:System.Windows.Media.MediaTimeline> （ <xref:System.Windows.Media.Animation.Timeline> 如 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 属性）来指定何时启动 <xref:System.Windows.Controls.MediaElement> （开始播放媒体）。</span><span class="sxs-lookup"><span data-stu-id="99c25-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="99c25-109">它还使用 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 属性来指定有效的时间长度 <xref:System.Windows.Controls.MediaElement> （媒体播放时间）。</span><span class="sxs-lookup"><span data-stu-id="99c25-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="99c25-110">有关 <xref:System.Windows.Media.Animation.Timeline> 将对象与结合使用的详细信息 <xref:System.Windows.Media.Animation.Storyboard> ，请参阅[情节提要概述](storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99c25-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="99c25-111">此示例演示如何创建使用的简单 media player <xref:System.Windows.Media.MediaTimeline> 来控制播放。</span><span class="sxs-lookup"><span data-stu-id="99c25-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="99c25-112">Media player 包括播放、暂停、恢复和停止按钮。</span><span class="sxs-lookup"><span data-stu-id="99c25-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="99c25-113">播放机还具有一个 <xref:System.Windows.Controls.Slider> 充当进度栏的控件。</span><span class="sxs-lookup"><span data-stu-id="99c25-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="99c25-114">下面的示例 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 为 media player 创建。</span><span class="sxs-lookup"><span data-stu-id="99c25-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="99c25-115">下面的示例为进度栏创建功能。</span><span class="sxs-lookup"><span data-stu-id="99c25-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="99c25-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99c25-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="99c25-117">控制 MediaElement（播放、暂停、停止、音量和速度）</span><span class="sxs-lookup"><span data-stu-id="99c25-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="99c25-118">演示图板概述</span><span class="sxs-lookup"><span data-stu-id="99c25-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="99c25-119">关键帧动画概述</span><span class="sxs-lookup"><span data-stu-id="99c25-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="99c25-120">动画概述</span><span class="sxs-lookup"><span data-stu-id="99c25-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="99c25-121">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="99c25-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="99c25-122">图形和多媒体</span><span class="sxs-lookup"><span data-stu-id="99c25-122">Graphics and Multimedia</span></span>](index.md)
