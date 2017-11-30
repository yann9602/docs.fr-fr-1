---
title: "Comment : effectuer une liaison avec les résultats d'une requête LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e77a0c698dae0330877c54422c15e14c82376891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="43936-102">Comment : effectuer une liaison avec les résultats d'une requête LINQ</span><span class="sxs-lookup"><span data-stu-id="43936-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="43936-103">Cet exemple montre comment exécuter une requête LINQ, puis lier aux résultats.</span><span class="sxs-lookup"><span data-stu-id="43936-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43936-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="43936-104">Example</span></span>  
 <span data-ttu-id="43936-105">L’exemple suivant crée deux zones de liste.</span><span class="sxs-lookup"><span data-stu-id="43936-105">The following example creates two list boxes.</span></span> <span data-ttu-id="43936-106">La zone de liste contient trois éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="43936-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="43936-107">Sélectionner un élément dans la zone de liste appelle le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="43936-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="43936-108">Dans cet exemple, `Tasks` est une collection de `Task` objets.</span><span class="sxs-lookup"><span data-stu-id="43936-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="43936-109">Le `Task` classe a une propriété nommée `Priority`.</span><span class="sxs-lookup"><span data-stu-id="43936-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="43936-110">Ce gestionnaire d’événements s’exécute une requête LINQ qui retourne la collection de `Task` les objets qui ont la valeur de priorité sélectionnée, puis la définit comme le <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="43936-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="43936-111">La deuxième zone de liste est liée à la collection, car son <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a la valeur `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="43936-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="43936-112">Par conséquent, il affiche la collection retournée (selon le `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="43936-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43936-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43936-113">See Also</span></span>  
 [<span data-ttu-id="43936-114">Rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="43936-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="43936-115">Effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="43936-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="43936-116">Nouveautés de WPF version 4.5</span><span class="sxs-lookup"><span data-stu-id="43936-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="43936-117">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="43936-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="43936-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="43936-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
