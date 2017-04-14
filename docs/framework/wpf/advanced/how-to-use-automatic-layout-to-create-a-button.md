---
title: "Comment&#160;: utiliser la disposition automatique pour cr&#233;er un bouton | Microsoft Docs"
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
  - "disposition automatique, créer des boutons"
  - "contrôles Button, créer avec une disposition automatique"
  - "créer, boutons avec une disposition automatique"
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: utiliser la disposition automatique pour cr&#233;er un bouton
Cet exemple décrit comment utiliser la disposition automatique pour créer un bouton dans une application localisable.  
  
 La localisation d'une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] peut prendre beaucoup de temps.  En plus de traduire le texte, les localisateurs doivent souvent redimensionner et repositionner des éléments.  Dans le passé, il fallait faire des ajustements pour chaque langue dans laquelle l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] était adaptée.  Désormais, les fonctions de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous permettent de concevoir des éléments qui réduisent les ajustements nécessaires.  L'approche consistant à écrire des applications qui sont plus faciles à redimensionner et à repositionner est appelée `automatic layout`.  
  
 Les deux exemples [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants créent des applications qui instancient un bouton ; un avec le texte en anglais et l'autre avec le texte en espagnol.  Notez que le code est identique, sauf pour le texte ; le bouton est ajusté pour contenir le texte.  
  
## Exemple  
 [!code-xml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Le graphique suivant illustre la sortie des exemples de code.  
  
 ![Même bouton avec le texte dans différentes langues](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Bouton redimensionnable automatiquement  
  
## Voir aussi  
 [Vue d'ensemble de l'utilisation de la disposition automatique](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [Utiliser une grille pour la disposition automatique](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)