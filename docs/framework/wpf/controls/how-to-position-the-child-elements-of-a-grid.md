---
title: "Comment&#160;: positionner les &#233;l&#233;ments enfants d&#39;une grille | Microsoft Docs"
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
  - "Grid (contrôle), positionner des éléments enfants"
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: positionner les &#233;l&#233;ments enfants d&#39;une grille
Cet exemple montre comment utiliser les méthodes get et set définies sur <xref:System.Windows.Controls.Grid> pour positionner des éléments enfants.  
  
## Exemple  
 L'exemple suivant définit un élément <xref:System.Windows.Controls.Grid> parent \(`grid1`\) qui comporte trois colonnes et trois lignes.  Un élément <xref:System.Windows.Shapes.Rectangle> enfant \(`rect1`\) est ajouté au <xref:System.Windows.Controls.Grid> à la position de colonne zéro et à la position de ligne zéro.  Les éléments <xref:System.Windows.Controls.Button> représentent des méthodes qui peuvent être appelées pour repositionner l'élément <xref:System.Windows.Shapes.Rectangle> dans le <xref:System.Windows.Controls.Grid>.  Lorsqu'un utilisateur clique sur un bouton, la méthode associée est activée.  
  
 [!code-xml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 L'exemple de code\-behind suivant gère les méthodes que les événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de bouton déclenchent.  L'exemple écrit ces appels de méthode aux éléments <xref:System.Windows.Controls.TextBlock> qui utilisent des méthodes get associées pour sortir les nouvelles valeurs de propriété comme chaînes.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)