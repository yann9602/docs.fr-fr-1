---
title: "Comment&#160;: obtenir ou d&#233;finir des propri&#233;t&#233;s de positionnement de la zone de dessin | Microsoft Docs"
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
  - "Canvas (contrôle), définir des propriétés de positionnement"
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: obtenir ou d&#233;finir des propri&#233;t&#233;s de positionnement de la zone de dessin
Cet exemple montre comment utiliser les méthodes de positionnement de l'élément <xref:System.Windows.Controls.Canvas> pour positionner le contenu enfant.  Cet exemple utilise le contenu d'un <xref:System.Windows.Controls.ListBoxItem> pour représenter des valeurs de positionnement et convertit les valeurs en instances de <xref:System.Double>, un argument requis pour le positionnement.  Les valeurs sont ensuite reconverties en chaînes et affichées sous forme de texte dans un élément <xref:System.Windows.Controls.TextBlock> à l'aide de la méthode <xref:System.Windows.Controls.Canvas.GetLeft%2A>.  
  
## Exemple  
 L'exemple suivant crée un élément <xref:System.Windows.Controls.ListBox> contenant onze éléments <xref:System.Windows.Controls.ListBoxItem> sélectionnables.  L'événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> déclenche la méthode personnalisée `ChangeLeft`, définie par le bloc de code suivant.  
  
 Chaque <xref:System.Windows.Controls.ListBoxItem> représente une valeur <xref:System.Double> qui est l'un des arguments que la méthode <xref:System.Windows.Controls.Canvas.SetLeft%2A> de <xref:System.Windows.Controls.Canvas> accepte.  Pour utiliser un <xref:System.Windows.Controls.ListBoxItem> afin de représenter une instance de <xref:System.Double>, vous devez d'abord convertir <xref:System.Windows.Controls.ListBoxItem> en type de données correct.  
  
 [!code-xml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Lorsqu'un utilisateur modifie la sélection <xref:System.Windows.Controls.ListBox>, la méthode personnalisée `ChangeLeft` est appelée.  Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un objet <xref:System.Windows.LengthConverter> qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.ListBoxItem> en une instance de <xref:System.Double> \(notez que cette valeur a déjà été convertie en <xref:System.String> à l'aide de la méthode <xref:System.Windows.Controls.Control.ToString%2A>\).  Cette valeur est ensuite repassée aux méthodes <xref:System.Windows.Controls.Canvas.SetLeft%2A> et <xref:System.Windows.Controls.Canvas.GetLeft%2A> de <xref:System.Windows.Controls.Canvas> pour modifier la position de l'objet `text1`.  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.ListBoxItem>   
 <xref:System.Windows.LengthConverter>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)