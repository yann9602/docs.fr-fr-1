---
title: "Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection"
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
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751025470b566ef1e735e4ddd192cfd8fc354ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="e4dfc-102">Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="e4dfc-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="e4dfc-103">Dans un scénario maître / détail simple, vous avez lié aux données <xref:System.Windows.Controls.ItemsControl> comme un <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="e4dfc-104">En fonction de la sélection de l’utilisateur, afficher plus d’informations sur l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="e4dfc-105">Cet exemple montre comment implémenter ce scénario.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4dfc-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4dfc-106">Example</span></span>  
 <span data-ttu-id="e4dfc-107">Dans cet exemple, `People` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="e4dfc-108">Cela `Person` classe contient trois propriétés : `FirstName`, `LastName`, et `HomeTown`, du type `string`.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="e4dfc-109">Le <xref:System.Windows.Controls.ContentControl> utilise les éléments suivants <xref:System.Windows.DataTemplate> qui définit comment les informations d’un `Person` est présenté :</span><span class="sxs-lookup"><span data-stu-id="e4dfc-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="e4dfc-110">Voici une capture d’écran d’illustre l’exemple.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="e4dfc-111">Le <xref:System.Windows.Controls.ContentControl> présente les autres propriétés de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="e4dfc-112">![Liaison à une collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="e4dfc-112">![Binding to a collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="e4dfc-113">Les deux choses à noter dans cet exemple sont :</span><span class="sxs-lookup"><span data-stu-id="e4dfc-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="e4dfc-114">Le <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.ContentControl> liés à la même source.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="e4dfc-115">Le <xref:System.Windows.Data.Binding.Path%2A> propriétés des deux liaisons ne sont pas spécifiées, car les deux contrôles créent une liaison à l’objet d’ensemble de la collection.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="e4dfc-116">Vous devez définir le <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriété `true` pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="e4dfc-117">Définition de cette propriété garantit que l’élément sélectionné est toujours défini en tant que le <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="e4dfc-118">Vous pouvez également, si le <xref:System.Windows.Controls.ListBox> obtient ses données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="e4dfc-119">Notez que la `Person` substitue le `ToString` méthode la façon suivante.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="e4dfc-120">Par défaut, le <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet dans la collection liée.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="e4dfc-121">C’est pourquoi chaque `Person` apparaît sous la forme d’un nom dans la <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="e4dfc-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="e4dfc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4dfc-122">See Also</span></span>  
 [<span data-ttu-id="e4dfc-123">Utiliser le modèle maître/détail avec des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="e4dfc-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [<span data-ttu-id="e4dfc-124">Utiliser le modèle maître/détail avec des données XML hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="e4dfc-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [<span data-ttu-id="e4dfc-125">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="e4dfc-125">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e4dfc-126">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="e4dfc-126">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="e4dfc-127">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="e4dfc-127">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
