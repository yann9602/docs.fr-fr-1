---
title: "Comment&#160;: utiliser la propri&#233;t&#233; BetweenShowDelay | Microsoft Docs"
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
  - "BetweenShowDelay (propriété de temps)"
  - "ToolTip (contrôle), BetweenShowDelay (propriété de temps)"
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: utiliser la propri&#233;t&#233; BetweenShowDelay
Cet exemple montre comment utiliser la propriété temporelle <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> afin que les info\-bulles apparaissent rapidement, avec peu ou pas de délai, lorsqu'un utilisateur déplace directement le pointeur de la souris d'une info\-bulle à une autre.  
  
## Exemple  
 Dans l'exemple suivant, la propriété <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> a la valeur une seconde \(1 000 millisecondes\) et <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> a la valeur deux secondes \(2 000 millisecondes\) pour les info\-bulles des deux contrôles <xref:System.Windows.Shapes.Ellipse>.  Si vous affichez l'info\-bulle de l'une des ellipses et qu'ensuite vous déplacez le pointeur de la souris vers une autre ellipse dans les deux secondes en marquant une pause, l'info\-bulle de la deuxième ellipse s'affiche immédiatement.  
  
 Dans l'un ou l'autre des scénarios suivants, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> s'applique, obligeant l'info\-bulle de la deuxième ellipse à attendre une seconde avant d'apparaître :  
  
-   Si vous mettez plus de deux secondes à vous déplacer vers le deuxième bouton.  
  
-   Si l'info\-bulle n'est pas visible dès le début de l'intervalle de temps pour la première ellipse.  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [Vue d'ensemble de l'info\-bulle](../../../../docs/framework/wpf/controls/tooltip-overview.md)