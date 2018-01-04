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
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="f0a6e-102">Comment : trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="f0a6e-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="f0a6e-103">Cet exemple montre comment créer une vue d’une collection de données en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0a6e-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="f0a6e-104">Les vues permettent pour les fonctionnalités de regroupement, le tri, filtrage et la notion d’un élément actuel.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a6e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0a6e-105">Example</span></span>  
 <span data-ttu-id="f0a6e-106">Dans l’exemple suivant, la ressource statique nommée *place* est défini comme une collection de *Place* objets, dans lequel chaque *Place* objet se compose d’un nom de ville et le état.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="f0a6e-107">Le préfixe *src* est mappé à l’espace de noms dans lequel la source de données *emplacements* est défini.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="f0a6e-108">Le préfixe *scm* est mappé à `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` et *dat* mappe à `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="f0a6e-109">L’exemple suivant crée une vue de la collecte de données qui est triée par nom de ville et regroupée par l’état.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="f0a6e-110">La vue peut ensuite être une source de liaison, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f0a6e-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="f0a6e-111">Pour les liaisons aux données XML définies dans un <xref:System.Windows.Data.XmlDataProvider> ressource, faites précéder le nom XML avec un symbole @.</span><span class="sxs-lookup"><span data-stu-id="f0a6e-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="f0a6e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0a6e-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="f0a6e-113">Obtenir la vue par défaut d'une collection de données</span><span class="sxs-lookup"><span data-stu-id="f0a6e-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="f0a6e-114">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="f0a6e-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f0a6e-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="f0a6e-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
