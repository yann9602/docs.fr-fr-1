---
title: "Comment&#160;: contr&#244;ler un MediaElement (lecture, pause, arr&#234;t, volume et vitesse) | Microsoft Docs"
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
  - "contrôler la lecture de médias"
  - "média, contrôler la lecture de"
  - "multimédias, contrôler la lecture de médias"
  - "lecture de médias, contrôler"
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: contr&#244;ler un MediaElement (lecture, pause, arr&#234;t, volume et vitesse)
L'exemple suivant indique comment contrôler la lecture d'un média à l'aide d'un <xref:System.Windows.Controls.MediaElement>.  L'exemple crée un lecteur multimédia simple qui vous permet de lire, mettre en pause, arrêter et accéder aux pistes suivante et précédente ainsi que de régler le volume et la vitesse.  
  
## Exemple  
 Le code suivant crée l'interface utilisateur.  
  
> [!NOTE]
>  Pour que vous puissiez arrêter, mettre en pause et lire le média de manière interactive, la propriété <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> de <xref:System.Windows.Controls.MediaElement> doit avoir la valeur `Manual`.  
  
 [!code-xml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## Exemple  
 Le code suivant implémente la fonctionnalité des exemples de contrôles d'interface utilisateur.  Les méthodes <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A> et <xref:System.Windows.Controls.MediaElement.Stop%2A> sont utilisées pour lire, mettre en pause et arrêter le média, respectivement.  La modification de la propriété <xref:System.Windows.Controls.MediaElement.Position%2A> de <xref:System.Windows.Controls.MediaElement> vous permet de naviguer sur le média.  Enfin, les propriétés <xref:System.Windows.Controls.MediaElement.Volume%2A> et <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> sont utilisées pour régler le volume et la vitesse de lecture des médias.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## Voir aussi  
 [Contrôler un MediaElement à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)