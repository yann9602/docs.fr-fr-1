---
title: "Comment&#160;: effectuer une liaison avec les r&#233;sultats d&#39;une requ&#234;te LINQ | Microsoft Docs"
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
  - "lier aux résultats d'une requête LINQ (WPF)"
  - "exécuter une requête LINQ (WPF), lier aux résultats"
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: effectuer une liaison avec les r&#233;sultats d&#39;une requ&#234;te LINQ
Cet exemple montre comment exécuter une requête LINQ, puis créer une liaison avec les résultats.  
  
## Exemple  
 L'exemple suivant crée deux zones de liste.  La première zone de liste contient trois éléments de liste.  
  
 [!code-xml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 La sélection d'un élément dans la première zone de liste appelle le gestionnaire d'événements suivant.  Dans cet exemple, `Tasks` est une collection d'objets `Task`.  La classe `Task` possède une propriété appelée `Priority`.  Ce gestionnaire d'événements exécute une requête LINQ qui retourne la collection des objets `Task` possédant la valeur de priorité sélectionnée, puis la définit comme valeur de <xref:System.Windows.FrameworkElement.DataContext%2A> :  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 La seconde zone de liste est liée à cette collection parce que sa valeur <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est `{Binding}`.  En conséquence, elle affiche la collection retournée \(selon le `myTaskTemplate`<xref:System.Windows.DataTemplate>\).  
  
## Voir aussi  
 [Rendre des données disponibles pour la liaison en XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)   
 [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [Nouveautés de WPF version 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)