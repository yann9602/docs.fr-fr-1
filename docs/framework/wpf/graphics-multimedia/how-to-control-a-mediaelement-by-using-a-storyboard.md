---
title: "Comment : contrôler un MediaElement à l'aide d'un storyboard"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f52801ee3704c13ec5213cfc54b6392baa97e245
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Comment : contrôler un MediaElement à l'aide d'un storyboard
Cet exemple montre comment contrôler une <xref:System.Windows.Controls.MediaElement> en utilisant un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Exemple  
 Lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> pour contrôler le minutage d’une <xref:System.Windows.Controls.MediaElement>, les fonctionnalités sont identiques à celles des autres <xref:System.Windows.Media.Animation.Timeline> objets, tels que les animations. Par exemple, un <xref:System.Windows.Media.MediaTimeline> utilise <xref:System.Windows.Media.Animation.Timeline> propriétés, telles que le <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriété pour indiquer quand commencer un <xref:System.Windows.Controls.MediaElement> (Démarrer la lecture du média). Elle utilise également le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété pour spécifier la durée pendant laquelle le <xref:System.Windows.Controls.MediaElement> est actif (durée de lecture du média). Pour plus d’informations sur l’utilisation de <xref:System.Windows.Media.Animation.Timeline> objets avec un <xref:System.Windows.Media.Animation.Storyboard>, consultez [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Cet exemple montre comment créer un lecteur multimédia simple qui utilise un <xref:System.Windows.Media.MediaTimeline> pour contrôler la lecture. Le lecteur multimédia comprend play, suspendre, reprendre et arrêter des boutons. Le lecteur a également un <xref:System.Windows.Controls.Slider> contrôle qui agit comme une barre de progression.  
  
 L’exemple suivant crée le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du lecteur multimédia.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 L’exemple suivant crée les fonctionnalités de la barre de progression.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Contrôler un MediaElement (lecture, pause, arrêt, volume et vitesse)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
