---
title: "Comment&#160;: utiliser une grille pour la disposition automatique | Microsoft Docs"
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
  - "disposition automatique, utilisation de la grille"
  - "grilles, disposition automatique"
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: utiliser une grille pour la disposition automatique
Cet exemple décrit comment utiliser une grille lorsque la disposition automatique est employée pour créer une application localisable.  
  
 La localisation d'une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] peut prendre beaucoup de temps.  En plus de traduire le texte, les localisateurs doivent souvent redimensionner et repositionner des éléments.  Dans le passé, il fallait faire des ajustements pour chaque langue dans laquelle l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] était adaptée.  Désormais, les fonctions de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous permettent de concevoir des éléments qui réduisent les ajustements nécessaires.  L'approche consistant à écrire des applications qui sont plus faciles à redimensionner et à repositionner est appelée `auto layout`.  
  
 L'exemple [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant illustre l'utilisation d'une grille pour positionner des boutons et du texte.  Remarquez que la valeur définie pour la hauteur et la largeur des cellules est `Auto`, c'est\-à\-dire que la cellule qui contient le bouton imagé s'adapte à cette image.  Comme l'élément <xref:System.Windows.Controls.Grid> peut s'adapter à son contenu, il peut s'avérer utile lorsque la disposition automatique est employée pour concevoir des applications localisables.  
  
## Exemple  
 L'exemple suivant montre comment utiliser une grille.  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Le graphique suivant illustre la sortie de l'exemple de code.  
  
 ![Exemple de grille](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
Grille  
  
## Voir aussi  
 [Vue d'ensemble de l'utilisation de la disposition automatique](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [Utiliser la disposition automatique pour créer un bouton](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)