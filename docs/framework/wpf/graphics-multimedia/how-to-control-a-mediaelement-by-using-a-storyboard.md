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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>如何：使用演示图板控制 MediaElement
此示例演示如何使用中的来控制 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 。  
  
## <a name="example"></a>示例  
 当使用中的 <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> 来控制的时间时 <xref:System.Windows.Controls.MediaElement> ，该功能与其他对象（如动画）的功能相同 <xref:System.Windows.Media.Animation.Timeline> 。 例如，使用属性 <xref:System.Windows.Media.MediaTimeline> （ <xref:System.Windows.Media.Animation.Timeline> 如 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 属性）来指定何时启动 <xref:System.Windows.Controls.MediaElement> （开始播放媒体）。 它还使用 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 属性来指定有效的时间长度 <xref:System.Windows.Controls.MediaElement> （媒体播放时间）。 有关 <xref:System.Windows.Media.Animation.Timeline> 将对象与结合使用的详细信息 <xref:System.Windows.Media.Animation.Storyboard> ，请参阅[情节提要概述](storyboards-overview.md)。  
  
 此示例演示如何创建使用的简单 media player <xref:System.Windows.Media.MediaTimeline> 来控制播放。 Media player 包括播放、暂停、恢复和停止按钮。 播放机还具有一个 <xref:System.Windows.Controls.Slider> 充当进度栏的控件。  
  
 下面的示例 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 为 media player 创建。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 下面的示例为进度栏创建功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [控制 MediaElement（播放、暂停、停止、音量和速度）](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [演示图板概述](storyboards-overview.md)
- [关键帧动画概述](key-frame-animations-overview.md)
- [动画概述](animation-overview.md)
- [操作指南主题](audio-and-video-how-to-topics.md)
- [图形和多媒体](index.md)
