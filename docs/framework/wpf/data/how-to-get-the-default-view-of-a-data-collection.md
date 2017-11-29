---
title: "Comment : obtenir la vue par défaut d'une collection de données"
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
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d1ababcb7a00496b59005b5e90f875511fefc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="c2c9e-102">Comment : obtenir la vue par défaut d'une collection de données</span><span class="sxs-lookup"><span data-stu-id="c2c9e-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="c2c9e-103">Les vues permettent à la même collection de données de différentes façons, en fonction de tri, de filtrage ou de critères de regroupement.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="c2c9e-104">Chaque collection a un affichage par défaut partagé, qui est utilisé comme source de liaison réelle lorsqu’une liaison spécifie une collection comme sa source.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="c2c9e-105">Cet exemple montre comment obtenir la vue par défaut d’une collection.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c9e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2c9e-106">Example</span></span>  
 <span data-ttu-id="c2c9e-107">Pour créer la vue, vous avez besoin d’une référence d’objet à la collection.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="c2c9e-108">Cet objet de données peut être obtenu en faisant référence à votre propre objet code-behind, en obtenant le contexte de données, en obtenant une propriété de la source de données, ou en obtenant une propriété de la liaison.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="c2c9e-109">Cet exemple montre comment obtenir le <xref:System.Windows.FrameworkElement.DataContext%2A> d’un objet de données et l’utiliser pour obtenir directement la collection par défaut afficher pour cette collection.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="c2c9e-110">Dans cet exemple, l’élément racine est un <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="c2c9e-111">Le <xref:System.Windows.FrameworkElement.DataContext%2A> a la valeur *myDataSource*, qui fait référence à un fournisseur de données est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de *commande* objets.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="c2c9e-112">Ou bien, vous pouvez instancier et lier à votre propre vue de collection à l’aide de la <xref:System.Windows.Data.CollectionViewSource> classe.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="c2c9e-113">Cette vue de collection est partagée uniquement par les contrôles liés directement.</span><span class="sxs-lookup"><span data-stu-id="c2c9e-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="c2c9e-114">Pour obtenir un exemple, consultez la section Comment créer une vue dans le [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2c9e-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c2c9e-115">Pour obtenir des exemples des fonctionnalités fournies par une vue de collection, consultez [trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrer des données dans une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), et [accédez via les objets d’un CollectionView de données](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="c2c9e-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c9e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2c9e-116">See Also</span></span>  
 [<span data-ttu-id="c2c9e-117">Trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="c2c9e-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="c2c9e-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="c2c9e-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
