---
title: "Comment : trier des données dans une vue"
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
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7467913f867ea0990ae85b0ad933c11f2fd271b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-data-in-a-view"></a>Comment : trier des données dans une vue
Cet exemple décrit comment trier les données dans une vue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un simple <xref:System.Windows.Controls.ListBox> et un <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements du bouton contient la logique pour trier les éléments dans le <xref:System.Windows.Controls.ListBox> dans l’ordre décroissant. Cela parce que l’ajout d’éléments à un <xref:System.Windows.Controls.ListBox> ainsi les ajoute à la <xref:System.Windows.Controls.ItemCollection> de la <xref:System.Windows.Controls.ListBox>, et <xref:System.Windows.Controls.ItemCollection> dérive la <xref:System.Windows.Data.CollectionView> classe. Si vous liez votre <xref:System.Windows.Controls.ListBox> à une collection en utilisant la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété, vous pouvez utiliser la même technique pour trier.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Tant que vous avez une référence à l’objet de vue, vous pouvez utiliser la même technique pour trier le contenu d’autres vues de collection. Pour obtenir un exemple illustrant comment obtenir une vue, consultez [obtenir la vue par défaut d’une Collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Pour un autre exemple, consultez [trier un GridView colonne lorsqu’un clic sur l’en-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Pour plus d’informations sur les vues, consultez la liaison aux Collections de [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Pour obtenir un exemple montrant comment appliquer la logique de tri dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consultez [de trier et de données de groupe à l’aide d’une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [Trier une colonne GridView lors d’un clic sur un en-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Filtrer les données d’une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
