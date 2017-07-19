---
title: "Comment&#160;: naviguer dans les objets d&#39;un CollectionView de donn&#233;es | Microsoft Docs"
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
  - "CollectionView, naviguer dans des objets"
  - "liaison de données, naviguer dans les objets d'un CollectionView de données"
  - "naviguer dans les objets d'un CollectionView de données"
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: naviguer dans les objets d&#39;un CollectionView de donn&#233;es
Les vues permettent d'afficher la même collection de données de différentes façons, selon les paramètres de tri, de filtrage ou de regroupement.  Les vues fournissent également un concept de pointeur d'enregistrement actif et permettent le déplacement du pointeur.  Cet exemple montre comment obtenir l'objet actif et naviguer parmi les objets d'une collection de données en utilisant la fonctionnalité fournie dans la classe <xref:System.Windows.Data.CollectionView>.  
  
## Exemple  
 Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.CollectionView> qui est une vue sur une collection liée.  
  
 Dans l'exemple suivant, `OnButton` est un gestionnaire d'événements des boutons `Previous` et `Next` d'une application, qui sont les boutons qui permettent à l'utilisateur de naviguer dans la collection de données.  Notez que les propriétés <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> et <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> indiquent si le pointeur d'enregistrement actif est arrivé respectivement au début et à la fin de la liste, afin que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> et <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> puissent être appelés de manière appropriée.  
  
 La propriété <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de la vue est castée en un `Order` afin de retourner l'élément d'ordre actif dans la collection.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [Trier et grouper des données à l'aide d'une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)