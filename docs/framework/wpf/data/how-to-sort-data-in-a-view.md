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
ms.openlocfilehash: 2c39cec8aaf12b268790c19751562b16fa34cfdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="110f9-102">Comment : trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="110f9-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="110f9-103">Cet exemple décrit comment trier les données dans une vue.</span><span class="sxs-lookup"><span data-stu-id="110f9-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="110f9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="110f9-104">Example</span></span>  
 <span data-ttu-id="110f9-105">L’exemple suivant crée un simple <xref:System.Windows.Controls.ListBox> et un <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="110f9-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="110f9-106">Le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements du bouton contient la logique pour trier les éléments dans le <xref:System.Windows.Controls.ListBox> dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="110f9-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="110f9-107">Cela parce que l’ajout d’éléments à un <xref:System.Windows.Controls.ListBox> ainsi les ajoute à la <xref:System.Windows.Controls.ItemCollection> de la <xref:System.Windows.Controls.ListBox>, et <xref:System.Windows.Controls.ItemCollection> dérive la <xref:System.Windows.Data.CollectionView> classe.</span><span class="sxs-lookup"><span data-stu-id="110f9-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="110f9-108">Si vous liez votre <xref:System.Windows.Controls.ListBox> à une collection en utilisant la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété, vous pouvez utiliser la même technique pour trier.</span><span class="sxs-lookup"><span data-stu-id="110f9-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="110f9-109">Tant que vous avez une référence à l’objet de vue, vous pouvez utiliser la même technique pour trier le contenu d’autres vues de collection.</span><span class="sxs-lookup"><span data-stu-id="110f9-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="110f9-110">Pour obtenir un exemple illustrant comment obtenir une vue, consultez [obtenir la vue par défaut d’une Collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="110f9-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="110f9-111">Pour un autre exemple, consultez [trier un GridView colonne lorsqu’un clic sur l’en-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="110f9-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="110f9-112">Pour plus d’informations sur les vues, consultez la liaison aux Collections de [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="110f9-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="110f9-113">Pour obtenir un exemple montrant comment appliquer la logique de tri dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consultez [de trier et de données de groupe à l’aide d’une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="110f9-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110f9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="110f9-114">See Also</span></span>  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [<span data-ttu-id="110f9-115">Trier une colonne GridView lors d’un clic sur un en-tête</span><span class="sxs-lookup"><span data-stu-id="110f9-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [<span data-ttu-id="110f9-116">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="110f9-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="110f9-117">Filtrer les données d’une vue</span><span class="sxs-lookup"><span data-stu-id="110f9-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="110f9-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="110f9-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
