---
title: "Comment&#160;: rechercher une horloge de fa&#231;on synchrone | Microsoft Docs"
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
  - "horloges, rechercher de façon synchrone"
  - "rechercher des horloges de façon synchrone"
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: rechercher une horloge de fa&#231;on synchrone
Utilisez la méthode <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> pour rechercher de façon synchrone une horloge à un point spécifique.  L'exemple suivant illustre les méthodes <xref:System.Windows.Media.Animation.ClockController.Seek%2A> et <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> d'un <xref:System.Windows.Media.Animation.ClockController>.  
  
 Cet exemple indique comment rechercher une <xref:System.Windows.Media.Animation.Clock>. Pour obtenir un exemple indiquant comment rechercher une table de montage séquentiel, consultez [Rechercher un storyboard de façon synchrone](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md).  
  
## Exemple  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]