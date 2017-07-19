---
title: "Comment&#160;: lire un m&#233;dia &#224; l&#39;aide d&#39;un VideoDrawing | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes, MediaPlayer"
  - "classes, VideoDrawing"
  - "MediaPlayer (classe)"
  - "lecture de médias"
  - "VideoDrawing (classe)"
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: lire un m&#233;dia &#224; l&#39;aide d&#39;un VideoDrawing
Pour lire un fichier audio ou vidéo, utilisez un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer>.  Il existe deux façons de charger et de lire un média.  La première consiste à utiliser un <xref:System.Windows.Media.MediaPlayer> et un <xref:System.Windows.Media.VideoDrawing>, et la seconde consiste à créer votre propre <xref:System.Windows.Media.MediaTimeline> à utiliser avec <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Lorsque vous distribuez un média avec votre application, vous ne pouvez pas utiliser un fichier multimédia comme ressource de projet, comme vous le feriez avec une image.  Dans votre fichier projet, vous devez plutôt affecter `Content` au type de média et `PreserveNewest` ou `Always` à `CopyToOutputDirectory`.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.VideoDrawing> et un <xref:System.Windows.Media.MediaPlayer> pour lire un fichier vidéo une seule fois.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Pour optimiser le contrôle du minutage du média, utilisez un <xref:System.Windows.Media.MediaTimeline> avec le <xref:System.Windows.Media.MediaPlayer> et des objets <xref:System.Windows.Media.VideoDrawing>.  <xref:System.Windows.Media.MediaTimeline> vous permet de spécifier si la vidéo doit se répéter.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.MediaTimeline> avec les objets <xref:System.Windows.Media.MediaPlayer> et <xref:System.Windows.Media.VideoDrawing> pour lire une vidéo à plusieurs reprises.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Notez que lorsque vous utilisez un <xref:System.Windows.Media.MediaTimeline>, vous utilisez le <xref:System.Windows.Media.Animation.ClockController> interactif retourné à partir de la propriété <xref:System.Windows.Media.Animation.Clock.Controller%2A> du <xref:System.Windows.Media.MediaClock> pour contrôler la lecture du média à la place des méthodes interactives du <xref:System.Windows.Media.MediaPlayer>.  
  
## Voir aussi  
 <xref:System.Windows.Media.VideoDrawing>   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)