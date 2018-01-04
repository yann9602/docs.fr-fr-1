---
title: "Comment : utiliser le modèle maître/détail avec des données hiérarchiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e392b47682d1bf53dc31073920bdf212fb7d997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="2f0dd-102">Comment : utiliser le modèle maître/détail avec des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="2f0dd-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="2f0dd-103">Cet exemple montre comment implémenter le scénario maître / détail.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0dd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f0dd-104">Example</span></span>  
 <span data-ttu-id="2f0dd-105">Dans cet exemple, `LeagueList` est une collection de `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="2f0dd-106">Chaque `League` a un `Name` et une collection de `Divisions`et chaque `Division` a un nom et une collection de `Teams`.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="2f0dd-107">Chaque `Team` a un nom d’équipe.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="2f0dd-108">Voici une capture d’écran de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="2f0dd-109">Le `Divisions` <xref:System.Windows.Controls.ListBox> suit automatiquement des sélections dans la `Leagues` <xref:System.Windows.Controls.ListBox> et afficher les données correspondantes.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="2f0dd-110">Le `Teams` <xref:System.Windows.Controls.ListBox> effectue le suivi des sélections dans les deux autres <xref:System.Windows.Controls.ListBox> contrôles.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="2f0dd-111">![Master &#45; exemple détail](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="2f0dd-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="2f0dd-112">Les deux choses à noter dans cet exemple sont :</span><span class="sxs-lookup"><span data-stu-id="2f0dd-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="2f0dd-113">Les trois <xref:System.Windows.Controls.ListBox> lient des contrôles à la même source.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="2f0dd-114">Vous définissez la <xref:System.Windows.Data.Binding.Path%2A> propriété de la liaison pour spécifier le niveau de données que vous souhaitez le <xref:System.Windows.Controls.ListBox> à afficher.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="2f0dd-115">Vous devez définir le <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriété `true` sur la <xref:System.Windows.Controls.ListBox> contrôles dont la sélection que vous effectuez le suivi.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="2f0dd-116">Définition de cette propriété garantit que l’élément sélectionné est toujours défini en tant que le <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="2f0dd-117">Vous pouvez également, si le <xref:System.Windows.Controls.ListBox> obtient ses données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="2f0dd-118">La technique est légèrement différente lorsque vous utilisez [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données.</span><span class="sxs-lookup"><span data-stu-id="2f0dd-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="2f0dd-119">Pour obtenir un exemple, consultez [utiliser le modèle maître / détail avec des données XML hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="2f0dd-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0dd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f0dd-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="2f0dd-121">Effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="2f0dd-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="2f0dd-122">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="2f0dd-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="2f0dd-123">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="2f0dd-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="2f0dd-124">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2f0dd-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
