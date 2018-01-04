---
title: "Comment : filtrer les données d'une vue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17b7fc68319552a7b31d5eaf7826146de5c41aa5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-data-in-a-view"></a>Comment : filtrer les données d'une vue
Cet exemple montre comment filtrer des données dans une vue.  
  
## <a name="example"></a>Exemple  
 Pour créer un filtre, définissez une méthode qui fournit la logique de filtrage. La méthode est utilisée comme un rappel et accepte un paramètre de type `object`. La méthode suivante retourne tous les le `Order` objets avec le `filled` propriété définie sur « Non », filtre le reste des objets.  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Vous pouvez ensuite appliquer le filtre, comme indiqué dans l’exemple suivant. Dans cet exemple, `myCollectionView` est un <xref:System.Windows.Data.ListCollectionView> objet.  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Pour annuler le filtrage, vous pouvez définir le <xref:System.Windows.Data.CollectionView.Filter%2A> propriété `null`:  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Pour plus d’informations sur la façon de créer ou d’obtenir une vue, consultez [obtenir la vue par défaut d’une Collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Pour obtenir un exemple complet, consultez [de tri et de filtrage des éléments dans une vue, exemple](http://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Si votre objet de vue provient d’un <xref:System.Windows.Data.CollectionViewSource> de l’objet, vous appliquez la logique de filtrage en définissant un gestionnaire d’événements pour le <xref:System.Windows.Data.CollectionViewSource.Filter> événement. Dans l’exemple suivant, `listingDataView` est une instance de <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 L’exemple suivant montre l’implémentation de l’exemple `ShowOnlyBargainsFilter` Gestionnaire d’événements de filtre. Ce gestionnaire d’événements utilise le <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> propriété à filtrer `AuctionItem` objets qui ont un `CurrentPrice` de $25 ou plus.  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
