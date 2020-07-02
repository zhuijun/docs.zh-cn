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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>如何：控制 MediaElement（播放、暂停、停止、音量和速度）
下面的示例演示如何使用控制媒体的播放 <xref:System.Windows.Controls.MediaElement> 。 该示例创建了一个简单的 media player，使你可以在媒体中播放、暂停、停止和向后跳过，以及调整音量和速度比。  
  
## <a name="example"></a>示例  
 下面的代码创建 UI。  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>的属性 <xref:System.Windows.Controls.MediaElement> 必须设置为，以便 `Manual` 能够以交互方式停止、暂停和播放媒体。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>示例  
 下面的代码实现了示例 UI 控件的功能。 <xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A> 和 <xref:System.Windows.Controls.MediaElement.Stop%2A> 方法用于分别播放、暂停和停止媒体。 通过更改 <xref:System.Windows.Controls.MediaElement.Position%2A> 的属性， <xref:System.Windows.Controls.MediaElement> 可以在媒体中跳过。 最后， <xref:System.Windows.Controls.MediaElement.Volume%2A> 和 <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> 属性用于调整媒体的音量和播放速度。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>另请参阅

- [使用情节提要控制 MediaElement](how-to-control-a-mediaelement-by-using-a-storyboard.md)
