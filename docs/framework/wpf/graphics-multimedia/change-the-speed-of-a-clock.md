---
title: "Comment : modifier la vitesse d'une horloge sans modifier la vitesse de sa chronologie"
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
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5421ed8b45c21e229d6c2682703cd9c7ee486e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>Comment : modifier la vitesse d'une horloge sans modifier la vitesse de sa chronologie
A <xref:System.Windows.Media.Animation.ClockController> l’objet <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> propriété permet de modifier la vitesse d’un <xref:System.Windows.Media.Animation.Clock> sans modifier le <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> de l’horloge <xref:System.Windows.Media.Animation.Timeline>. Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.ClockController> permet de modifier de manière interactive le <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> d’une horloge. Le <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> événement et de l’horloge <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> propriété sont utilisés pour afficher la vitesse globale actuelle de l’horloge chaque fois que son interactif <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> est modifiée.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
