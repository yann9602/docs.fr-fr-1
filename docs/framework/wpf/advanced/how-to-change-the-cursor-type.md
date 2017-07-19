---
title: "Comment&#160;: modifier le type de curseur | Microsoft Docs"
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
  - "curseur (pointeur de la souris)"
  - "pointeur de la souris (curseur), type de curseur"
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: modifier le type de curseur
Cet exemple indique comment modifier le <xref:System.Windows.Input.Cursor> du pointeur de la souris pour un élément spécifique et pour l'application.  
  
 Cet exemple se compose d'un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et d'un fichier code\-behind.  
  
## Exemple  
 L'interface utilisateur est créée ; elle est constituée d'un <xref:System.Windows.Controls.ComboBox> pour sélectionner le <xref:System.Windows.Input.Cursor> souhaité, d'une paire d'objets <xref:System.Windows.Controls.RadioButton> pour déterminer si la modification de curseur s'applique à un seul élément ou à toute l'application, ainsi que d'un <xref:System.Windows.Controls.Border> qui correspond à l'élément auquel le nouveau curseur est appliqué.  
  
 [!code-xml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Le code\-behind suivant crée un gestionnaire d'événements <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> appelé lorsque le type de curseur est modifié dans <xref:System.Windows.Controls.ComboBox>.  Une instruction switch effectue un filtre sur le nom de curseur et définit la propriété <xref:System.Windows.FrameworkElement.Cursor%2A> sur le <xref:System.Windows.Controls.Border> nommé *DisplayArea*.  
  
 Si la modification de curseur a pour valeur "Entire Application", la propriété <xref:System.Windows.Input.Mouse.OverrideCursor%2A> est définie sur la propriété <xref:System.Windows.FrameworkElement.Cursor%2A> du contrôle <xref:System.Windows.Controls.Border>.  Cette opération force la modification du curseur pour toute l'application.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## Voir aussi  
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)