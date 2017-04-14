---
title: "Comment&#160;: obtenir la vue par d&#233;faut d&#39;une collection de donn&#233;es | Microsoft Docs"
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
  - "créer, vues de collections de données"
  - "liaison de données, créer des vues de collections de données"
  - "collections de données, créer des vues de"
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: obtenir la vue par d&#233;faut d&#39;une collection de donn&#233;es
Les vues permettent d'afficher la même collection de données de différentes façons, selon les critères de tri, de filtrage ou de regroupement.  Chaque collection a un affichage par défaut partagé, utilisé comme source de liaison réelle lorsqu'une liaison spécifie une collection comme sa source.  Cet exemple montre comment obtenir la vue par défaut d'une collection  
  
## Exemple  
 Pour créer la vue, vous avez besoin d'une référence d'objet vers la collection.  Vous pouvez obtenir cet objet de données en référençant votre propre objet code\-behind, en obtenant le contexte de données ou bien en obtenant une propriété de la source de données ou de la liaison.  Cet exemple montre comment obtenir le <xref:System.Windows.FrameworkElement.DataContext%2A> d'un objet de données et l'utiliser pour obtenir directement la vue de collection par défaut de cette collection.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Dans cet exemple, l'élément racine est un <xref:System.Windows.Controls.StackPanel>.  Le <xref:System.Windows.FrameworkElement.DataContext%2A> a la valeur *myDataSource*, qui fait référence à un fournisseur de données lequel est une <xref:System.Collections.ObjectModel.ObservableCollection%601> d'objets d'*ordre*.  
  
 [!code-xml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Vous avez également la possibilité d'instancier et de lier votre propre vue de collection au moyen de la classe <xref:System.Windows.Data.CollectionViewSource>.  Cette vue de collection est partagée uniquement par les contrôles que y sont liés directement.  Pour obtenir un exemple, consultez la section Comment créer une vue sous [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Pour obtenir des exemples des fonctionnalités offertes par une vue de collection, consultez [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md) et [Naviguer dans les objets d'un CollectionView de données](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## Voir aussi  
 [Trier et grouper des données à l'aide d'une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)