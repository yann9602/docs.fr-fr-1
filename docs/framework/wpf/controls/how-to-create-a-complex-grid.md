---
title: "Comment&#160;: cr&#233;er une grille complexe | Microsoft Docs"
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
  - "calendrier, créer"
  - "Grid (contrôle), créer, grille complexe"
  - "calendrier mensuel, créer"
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er une grille complexe
Cet exemple montre comment utiliser une <xref:System.Windows.Controls.Grid> pour créer une disposition qui ressemble à un calendrier mensuel.  
  
## Exemple  
 L'exemple suivant définit huit lignes et huit colonnes en utilisant les classes <xref:System.Windows.Controls.RowDefinition> et <xref:System.Windows.Controls.ColumnDefinition>.  Il utilise les propriétés jointes <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=fullName> et <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=fullName> avec des éléments <xref:System.Windows.Shapes.Rectangle> qui remplissent les arrière\-plans des différentes colonnes et lignes.  Cette conception est possible car plusieurs éléments peuvent exister dans chaque cellule d'une <xref:System.Windows.Controls.Grid>, une différence de principe entre <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Documents.Table>.  
  
 L'exemple utilise des dégradés verticaux pour <xref:System.Windows.Shapes.Shape.Fill%2A> les colonnes et les lignes afin d'améliorer la présentation visuelle et la lisibilité du calendrier.  Les éléments <xref:System.Windows.Controls.TextBlock> à style personnalisé représentent les dates et jours de la semaine.  Les éléments <xref:System.Windows.Controls.TextBlock> sont positionnés de manière absolue dans leurs cellules à l'aide de la propriété <xref:System.Windows.FrameworkElement.Margin%2A> et des propriétés d'alignement définies dans le style de l'application.  
  
 [!code-xml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Documents.TableCell>   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)