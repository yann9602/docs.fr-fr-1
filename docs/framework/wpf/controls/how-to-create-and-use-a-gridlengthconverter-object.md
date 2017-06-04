---
title: "Comment&#160;: cr&#233;er et utiliser un objet GridLengthConverter | Microsoft Docs"
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
  - "Grid (contrôle), créer, objets GridLengthConverter"
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er et utiliser un objet GridLengthConverter
## Exemple  
 L'exemple suivant montre comment créer et utiliser une instance de <xref:System.Windows.GridLengthConverter>.  L'exemple définit une méthode personnalisée appelée `changeCol` qui passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.GridLengthConverter> qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.ListBoxItem> en une instance de <xref:System.Windows.GridLength>.  La valeur convertie est ensuite retournée comme valeur de la propriété <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de l'élément <xref:System.Windows.Controls.ColumnDefinition>.  
  
 L'exemple définit également une deuxième méthode personnalisée, appelée `changeColVal`.  Cette méthode personnalisée convertit la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> d'un <xref:System.Windows.Controls.Slider> en <xref:System.String>, puis retourne cette valeur à <xref:System.Windows.Controls.ColumnDefinition> comme <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de l'élément.  
  
 Notez qu'un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] séparé définit le contenu d'un <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.GridLengthConverter>   
 <xref:System.Windows.GridLength>