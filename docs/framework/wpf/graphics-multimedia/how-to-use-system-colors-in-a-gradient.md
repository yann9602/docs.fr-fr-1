---
title: "Comment&#160;: utiliser des couleurs syst&#232;me dans un d&#233;grad&#233; | Microsoft Docs"
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
  - "dégradés, couleurs système dans"
  - "couleurs système dans les dégradés"
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: utiliser des couleurs syst&#232;me dans un d&#233;grad&#233;
Pour utiliser une couleur système dans un dégradé, utilisez les propriétés statiques *\<CouleurSystème\>*Color et *\<CouleurSystème\>*ColorKey de la classe <xref:System.Windows.SystemColors> pour obtenir une référence à la couleur, où *\<CouleurSystème\>* correspond au nom de la couleur système souhaitée.  Utilisez la propriété *\<CouleurSystème\>*ColorKey pour créer une référence dynamique qui se met à jour automatiquement lorsque le thème du système change.  Sinon, utilisez la propriété *\<CouleurSystème\>*Color.  
  
## Exemple  
 L'exemple suivant utilise des ressources de couleurs système dynamiques pour créer un dégradé.  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 L'exemple suivant crée un dégradé à l'aide de ressources de couleurs système statiques.  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.SystemColors>   
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)