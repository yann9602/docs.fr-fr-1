---
title: "Comment&#160;: filtrer les donn&#233;es d&#39;une vue | Microsoft Docs"
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
  - "liaison de données, filtrer des données dans des vues"
  - "filtrer des données dans des vues"
  - "vues, filtrer des données"
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: filtrer les donn&#233;es d&#39;une vue
Cet exemple montre comment filtrer des données dans une vue.  
  
## Exemple  
 Pour créer un filtre, définissez une méthode qui fournit une logique de filtrage.  La méthode est utilisée comme rappel et accepte un paramètre de type `object`.  La méthode suivante retourne tous les objets dont la propriété `Order` `filled` a la valeur "Non", et filtre le reste des objets.  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Vous pouvez ensuite appliquer le filtre, comme illustré dans l'exemple suivant.  Dans cet exemple, `myCollectionView` est un objet <xref:System.Windows.Data.ListCollectionView>.  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Pour annuler le filtrage, vous pouvez affecter la valeur `null` à la propriété <xref:System.Windows.Data.CollectionView.Filter%2A> :  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Pour plus d'informations sur la création ou l'obtention d'une vue, consultez [Obtenir la vue par défaut d'une collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  Pour obtenir l'exemple complet, consultez [Tri et filtrage d'éléments dans une vue, exemple](http://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Si votre objet de vue provient d'un objet <xref:System.Windows.Data.CollectionViewSource>, vous pouvez appliquer la logique de filtrage en définissant un gestionnaire d'événements pour l'événement <xref:System.Windows.Data.CollectionViewSource.Filter>.  Dans l'exemple suivant, `listingDataView` est une instance de <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 L'exemple suivant illustre l'implémentation du gestionnaire d'événements de filtre `ShowOnlyBargainsFilter`.  Ce gestionnaire d'événements utilise la propriété <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> pour filtrer des objets `AuctionItem` dont le `CurrentPrice` est de $25 ou plus.  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## Voir aussi  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>   
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)