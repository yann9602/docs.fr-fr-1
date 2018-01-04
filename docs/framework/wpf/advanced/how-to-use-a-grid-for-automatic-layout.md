---
title: Guide pratique pour utiliser une grille pour la disposition automatique
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Guide pratique pour utiliser une grille pour la disposition automatique
Cet exemple décrit comment utiliser une grille quand vous tirez parti de la disposition automatique pour créer une application localisable.  
  
 Localisation d’un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] peut prendre beaucoup de temps. Les localisateurs doivent souvent redimensionner et repositionner les éléments, en plus de traduire le texte. Dans le passé chaque langue qu’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a été adaptée pour l’ajustement nécessaire. Désormais, avec les fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous pouvez concevoir des éléments qui réduisent les ajustements nécessaires. L’approche consistant à écrire des applications qui peuvent être plus facilement redimensionné et repositionné est appelée `auto layout`.  
  
 Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple illustre l’utilisation d’une grille pour positionner des boutons et du texte. Notez que la hauteur et la largeur des cellules sont définies pour `Auto`; par conséquent, la cellule qui contient le bouton avec une image s’ajuste à l’image. Étant donné que le <xref:System.Windows.Controls.Grid> élément peut ajuster à son contenu, il peut être utile lorsque vous effectuez l’approche de mise en page automatique pour concevoir des applications qui peuvent être localisées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser une grille.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Le graphique suivant montre la sortie générée par l’exemple de code.  
  
 ![Exemple de grille](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Grille  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’utilisation de la disposition automatique](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Utiliser la disposition automatique pour créer un bouton](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
