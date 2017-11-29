---
title: "Comment : grouper des éléments dans un ListView implémentant un GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30808e8ee0223c31085a65ff025fb188c0132057
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="949fc-102">Comment : grouper des éléments dans un ListView implémentant un GridView</span><span class="sxs-lookup"><span data-stu-id="949fc-102">How to: Group Items in a ListView That Implements a GridView</span></span>
<span data-ttu-id="949fc-103">Cet exemple montre comment afficher les groupes d’éléments dans le <xref:System.Windows.Controls.GridView> mode d’affichage d’un <xref:System.Windows.Controls.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="949fc-103">This example shows how to display groups of items in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="949fc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="949fc-104">Example</span></span>  
 <span data-ttu-id="949fc-105">Pour afficher les groupes d’éléments dans un <xref:System.Windows.Controls.ListView>, définir un <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="949fc-105">To display groups of items in a <xref:System.Windows.Controls.ListView>, define a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="949fc-106">L’exemple suivant montre un <xref:System.Windows.Data.CollectionViewSource> qui regroupe les éléments de données en fonction de la valeur de la `Catalog` champ de données.</span><span class="sxs-lookup"><span data-stu-id="949fc-106">The following example shows a <xref:System.Windows.Data.CollectionViewSource> that groups data items according to the value of the `Catalog` data field.</span></span>  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 <span data-ttu-id="949fc-107">L’exemple suivant définit la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pour le <xref:System.Windows.Controls.ListView> à le <xref:System.Windows.Data.CollectionViewSource> par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="949fc-107">The following example sets the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.ListView> to the <xref:System.Windows.Data.CollectionViewSource> that the previous example defines.</span></span> <span data-ttu-id="949fc-108">L’exemple définit également un <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> qui implémente un <xref:System.Windows.Controls.Expander> contrôle.</span><span class="sxs-lookup"><span data-stu-id="949fc-108">The example also defines a <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> that implements an <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a><span data-ttu-id="949fc-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="949fc-109">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="949fc-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="949fc-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="949fc-111">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="949fc-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="949fc-112">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="949fc-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
