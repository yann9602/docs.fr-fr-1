---
title: "Comment&#160;: contr&#244;ler une horloge de fa&#231;on interactive | Microsoft Docs"
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
  - "horloges, contrôler de manière interactive"
  - "contrôler des horloges de manière interactive"
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: contr&#244;ler une horloge de fa&#231;on interactive
La propriété <xref:System.Windows.Media.Animation.ClockController> d'un objet <xref:System.Windows.Media.Animation.Clock> vous permet de contrôler l'horloge de manière interactive : vous pouvez démarrer, suspendre, reprendre, rechercher, avancer l'horloge à sa période de remplissage et l'arrêter.  Vous ne pouvez contrôler de manière interactive que l'horloge racine d'une arborescence de minutage.  
  
> [!NOTE]
>  D'autres méthodes permettent de contrôler de manière interactive des animations qui ne requièrent pas que vous utilisiez directement des horloges : vous pouvez également utiliser des tables de montage séquentiel.  Les tables de montage séquentiel sont prises en charge dans le balisage et le code.  Pour obtenir un exemple, consultez [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ou [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 L'exemple suivant utilise plusieurs boutons pour contrôler une horloge d'animation de manière interactive.  
  
## Exemple  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## Voir aussi  
 [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)