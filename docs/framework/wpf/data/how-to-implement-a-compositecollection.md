---
title: "Comment&#160;: impl&#233;menter une classe CompositeCollection | Microsoft Docs"
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
  - "classes, CompositeCollection"
  - "liaison de données, CompositeCollection (classe)"
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: impl&#233;menter une classe CompositeCollection
## Exemple  
 L'exemple suivant indique comment afficher plusieurs collections et éléments comme une liste à l'aide de la classe <xref:System.Windows.Data.CompositeCollection>.  Dans cet exemple, `GreekGods` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> d'objets personnalisés `GreekGod`.  Les modèles de données sont définis de telle sorte que les objets `GreekGod` et les objets `GreekHero` apparaissent respectivement avec une couleur de premier plan or et cyan.  
  
 [!code-xml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## Voir aussi  
 <xref:System.Windows.Data.CollectionContainer>   
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>   
 <xref:System.Windows.Data.XmlDataProvider>   
 <xref:System.Windows.DataTemplate>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)