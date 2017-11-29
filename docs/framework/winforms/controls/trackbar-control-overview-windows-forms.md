---
title: "Vue d'ensemble du contrôle TrackBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccea982c45ab22a4b2ab81bc80c16dd472144bbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle TrackBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> contrôle (parfois également appelé contrôle « slider ») est utilisé pour naviguer dans une grande quantité d’informations ou d’ajuster visuellement un paramètre numérique. Le <xref:System.Windows.Forms.TrackBar> contrôle comporte deux parties : le curseur de défilement, également appelé un curseur et les marques de graduation. Le curseur est la partie qui peut être ajustée. Sa position correspond à la <xref:System.Windows.Forms.TrackBar.Value%2A> propriété. Les graduations sont des indicateurs visuels qui sont exécutées à intervalles réguliers. La barre de suivi se déplace dans les incréments que vous spécifiez. Par exemple, vous pouvez utiliser la barre de suivi pour contrôler la souris ou le taux de clignotement du curseur pour un système.  
  
## <a name="key-properties"></a>Principales propriétés  
 Les propriétés de clé de la <xref:System.Windows.Forms.TrackBar> contrôle sont <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, et <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>correspond à l’espacement des graduations. <xref:System.Windows.Forms.TrackBar.Minimum%2A>et <xref:System.Windows.Forms.TrackBar.Maximum%2A> sont les valeurs minimale et maximale pouvant être représentées sur la barre de suivi.  
  
 Deux autres propriétés importantes sont <xref:System.Windows.Forms.TrackBar.SmallChange%2A> et <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. La valeur de la <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propriété est le nombre de positions le curseur se déplace en réponse à disposer de la touche gauche ou droite. La valeur de la <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propriété est le nombre de positions le curseur se déplace en réponse lorsque la PAGE précédente ou PAGE suivante touche ou en réponse à la souris clique sur la barre de suivi de chaque côté du curseur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar, contrôle](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
