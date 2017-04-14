---
title: "Comment&#160;: g&#233;n&#233;rer une bo&#238;te de dialogue d&#39;interface utilisateur standard &#224; l&#39;aide de Grid | Microsoft Docs"
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
  - "boîtes de dialogue, créer"
  - "Grid (contrôle), créer, boîte de dialogue"
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: g&#233;n&#233;rer une bo&#238;te de dialogue d&#39;interface utilisateur standard &#224; l&#39;aide de Grid
Cet exemple montre comment créer une boîte de dialogue d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] standard à l'aide de l'élément <xref:System.Windows.Controls.Grid>.  
  
## Exemple  
 L'exemple suivant crée une boîte de dialogue identique à la boîte de dialogue **Exécuter** du système d'exploitation [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 L'exemple crée une <xref:System.Windows.Controls.Grid> et utilise les classes <xref:System.Windows.Controls.ColumnDefinition> et <xref:System.Windows.Controls.RowDefinition> pour définir cinq colonnes et quatre lignes.  
  
 Ensuite, l'exemple ajoute et positionne une <xref:System.Windows.Controls.Image>, `RunIcon.png` pour représenter l'image affichée dans la boîte de dialogue.  L'image est placée dans la première colonne, première ligne, de la <xref:System.Windows.Controls.Grid> \(angle supérieur gauche\).  
  
 Ensuite, l'exemple ajoute un élément <xref:System.Windows.Controls.TextBlock> à la première colonne, ce qui couvre les colonnes restantes de la première ligne.  Il ajoute un autre élément <xref:System.Windows.Controls.TextBlock> à la deuxième ligne de la première colonne, pour représenter la zone de texte **Ouvrir**.  Un <xref:System.Windows.Controls.TextBlock> suit et représente la zone de saisie de données.  
  
 Enfin, l'exemple ajoute trois éléments <xref:System.Windows.Controls.Button> à la dernière ligne, qui représentent les événements **OK**, **Annuler** et **Parcourir**.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.GridUnitType>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)