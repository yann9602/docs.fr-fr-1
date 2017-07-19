---
title: "Comment&#160;: contr&#244;ler un MediaElement &#224; l&#39;aide d&#39;un storyboard | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôler la lecture de médias, avec des storyboards"
  - "média, contrôler la lecture avec des storyboards"
  - "multimédias, contrôler la lecture de médias avec des storyboards"
  - "lecture de médias, contrôler avec des storyboards"
  - "Animations, contrôler la lecture de médias avec"
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: contr&#244;ler un MediaElement &#224; l&#39;aide d&#39;un storyboard
Cet exemple indique comment contrôler un <xref:System.Windows.Controls.MediaElement> à l'aide d'un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard>.  
  
## Exemple  
 Lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline> dans un <xref:System.Windows.Media.Animation.Storyboard> pour contrôler le minutage d'un <xref:System.Windows.Controls.MediaElement>, les fonctionnalités sont identiques à celles d'autres objets <xref:System.Windows.Media.Animation.Timeline>, tels que les animations.  Par exemple, un <xref:System.Windows.Media.MediaTimeline> utilise des propriétés <xref:System.Windows.Media.Animation.Timeline> telles que la propriété <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> pour spécifier le moment auquel démarrer un <xref:System.Windows.Controls.MediaElement> \(démarrer la lecture du média\).  Il utilise également la propriété <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pour spécifier la durée pendant laquelle <xref:System.Windows.Controls.MediaElement> est actif \(durée de lecture du média\).  Pour plus d'informations sur l'utilisation des objets <xref:System.Windows.Media.Animation.Timeline> avec un <xref:System.Windows.Media.Animation.Storyboard>, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Cet exemple indique comment créer un lecteur multimédia simple qui utilise un <xref:System.Windows.Media.MediaTimeline> pour contrôler la lecture.  Le lecteur multimédia inclut les boutons lire, pause, reprendre et arrêter.  Le lecteur dispose également d'un contrôle <xref:System.Windows.Controls.Slider> qui agit comme une barre de progression.  
  
 L'exemple suivant crée l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du lecteur multimédia.  
  
 [!code-xml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 L'exemple suivant crée les fonctionnalités de la barre de progression.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.MediaElement>   
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [Contrôler un MediaElement \(lecture, pause, arrêt, volume et vitesse\)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md)