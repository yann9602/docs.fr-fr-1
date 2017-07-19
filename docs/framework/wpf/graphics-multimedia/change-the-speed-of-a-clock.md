---
title: "Comment&#160;: modifier la vitesse d&#39;une horloge sans modifier la vitesse de sa chronologie | Microsoft Docs"
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
  - "horloges, modifier la vitesse des"
  - "vitesse d'horloge, modifier"
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: modifier la vitesse d&#39;une horloge sans modifier la vitesse de sa chronologie
La propriété <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> d'un objet <xref:System.Windows.Media.Animation.ClockController> vous permet de modifier la vitesse d'un <xref:System.Windows.Media.Animation.Clock> sans altérer le <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> du <xref:System.Windows.Media.Animation.Timeline> de l'horloge.  Dans l'exemple suivant, un <xref:System.Windows.Media.Animation.ClockController> est utilisé pour modifier de manière interactive le <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> d'une horloge.  L'événement <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> et la propriété <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> de l'horloge sont utilisés pour afficher la vitesse globale actuelle de l'horloge à chaque fois que son <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> interactif est modifié.  
  
## Exemple  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]