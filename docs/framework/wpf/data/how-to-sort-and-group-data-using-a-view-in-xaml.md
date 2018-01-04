---
title: "Comment : trier et grouper des données à l'aide d'une vue en XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bfa1941e6352372712debb5a5243bdd24810aac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Comment : trier et grouper des données à l'aide d'une vue en XAML
Cet exemple montre comment créer une vue d’une collection de données en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Les vues permettent pour les fonctionnalités de regroupement, le tri, filtrage et la notion d’un élément actuel.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la ressource statique nommée *place* est défini comme une collection de *Place* objets, dans lequel chaque *Place* objet se compose d’un nom de ville et le état. Le préfixe *src* est mappé à l’espace de noms dans lequel la source de données *emplacements* est défini. Le préfixe *scm* est mappé à `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` et *dat* mappe à `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 L’exemple suivant crée une vue de la collecte de données qui est triée par nom de ville et regroupée par l’état.  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 La vue peut ensuite être une source de liaison, comme dans l’exemple suivant :  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Pour les liaisons aux données XML définies dans un <xref:System.Windows.Data.XmlDataProvider> ressource, faites précéder le nom XML avec un symbole @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.CollectionViewSource>  
 [Obtenir la vue par défaut d'une collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
