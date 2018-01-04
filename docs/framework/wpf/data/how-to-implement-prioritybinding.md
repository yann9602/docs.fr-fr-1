---
title: "Comment : implémenter PriorityBinding"
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
helpviewer_keywords: data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b254867200897acad2868e396d152a5f9efcbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="7306d-102">Comment : implémenter PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="7306d-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="7306d-103"><xref:System.Windows.Data.PriorityBinding>dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionne en spécifiant une liste de liaisons.</span><span class="sxs-lookup"><span data-stu-id="7306d-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="7306d-104">La liste de liaisons est classée de priorité la plus élevée à la priorité la plus faible.</span><span class="sxs-lookup"><span data-stu-id="7306d-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="7306d-105">Si la liaison de priorité la plus élevée retourne une valeur avec succès lorsqu’il est traité puis il est jamais nécessaire pour traiter les autres liaisons dans la liste.</span><span class="sxs-lookup"><span data-stu-id="7306d-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="7306d-106">Il peut être le cas de la liaison de priorité la plus élevée prend beaucoup de temps à évaluer, la priorité la plus élevée suivante qui retourne une valeur avec succès est utilisée jusqu'à ce qu’une liaison d’une priorité plus élevée retourne une valeur avec succès.</span><span class="sxs-lookup"><span data-stu-id="7306d-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7306d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7306d-107">Example</span></span>  
 <span data-ttu-id="7306d-108">Pour illustrer comment <xref:System.Windows.Data.PriorityBinding> fonctionne, le `AsyncDataSource` objet a été créé avec les trois propriétés suivantes : `FastDP`, `SlowerDP`, et `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="7306d-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="7306d-109">L’accesseur get de `FastDP` retourne la valeur de la `_fastDP` membre de données.</span><span class="sxs-lookup"><span data-stu-id="7306d-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="7306d-110">L’accesseur get de `SlowerDP` attend trois secondes avant de retourner la valeur de la `_slowerDP` membre de données.</span><span class="sxs-lookup"><span data-stu-id="7306d-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="7306d-111">L’accesseur get de `SlowestDP` attend 5 secondes avant de retourner la valeur de la `_slowestDP` membre de données.</span><span class="sxs-lookup"><span data-stu-id="7306d-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7306d-112">Cet exemple est uniquement à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="7306d-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="7306d-113">Le [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recommandé par rapport à la définition des propriétés qui sont beaucoup plus lente qu’un ensemble de champs.</span><span class="sxs-lookup"><span data-stu-id="7306d-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="7306d-114">Pour plus d’informations, consultez [NIB : choix entre les propriétés et méthodes](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span><span class="sxs-lookup"><span data-stu-id="7306d-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="7306d-115">Le <xref:System.Windows.Controls.TextBlock.Text%2A> propriété est liée à la liste ci-dessus `AsyncDS` à l’aide de <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="7306d-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="7306d-116">Lorsque le moteur de liaison traite les <xref:System.Windows.Data.Binding> des objets, il commence par la première <xref:System.Windows.Data.Binding>, qui est lié à la `SlowestDP` propriété.</span><span class="sxs-lookup"><span data-stu-id="7306d-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="7306d-117">Lorsque cela <xref:System.Windows.Data.Binding> est traité, il ne retourne pas de valeur avec succès, car il est en veille pendant 5 secondes, par conséquent, la prochaine <xref:System.Windows.Data.Binding> élément est traité.</span><span class="sxs-lookup"><span data-stu-id="7306d-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="7306d-118">La prochaine <xref:System.Windows.Data.Binding> ne retourne pas de valeur avec succès, car il est en veille pendant 3 secondes.</span><span class="sxs-lookup"><span data-stu-id="7306d-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="7306d-119">Le moteur de liaison, puis déplace sur la prochaine <xref:System.Windows.Data.Binding> élément, qui est lié à la `FastDP` propriété.</span><span class="sxs-lookup"><span data-stu-id="7306d-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="7306d-120">Cela <xref:System.Windows.Data.Binding> retourne la valeur « rapide ».</span><span class="sxs-lookup"><span data-stu-id="7306d-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="7306d-121">Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « rapide ».</span><span class="sxs-lookup"><span data-stu-id="7306d-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="7306d-122">Après 3 secondes, la `SlowerDP` propriété retourne la valeur « Valeur plus lent ».</span><span class="sxs-lookup"><span data-stu-id="7306d-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="7306d-123">Le <xref:System.Windows.Controls.TextBlock> puis affiche la valeur « Valeur plus lent ».</span><span class="sxs-lookup"><span data-stu-id="7306d-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="7306d-124">Après 5 secondes, la `SlowestDP` propriété retourne la valeur « Les plus lents Value ».</span><span class="sxs-lookup"><span data-stu-id="7306d-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="7306d-125">Cette liaison a la priorité la plus élevée, car elle est répertoriée en premier.</span><span class="sxs-lookup"><span data-stu-id="7306d-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="7306d-126">Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « Les plus lents Value ».</span><span class="sxs-lookup"><span data-stu-id="7306d-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="7306d-127">Consultez <xref:System.Windows.Data.PriorityBinding> pour plus d’informations sur ce qui est considéré comme une valeur de retour réussite d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="7306d-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7306d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7306d-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7306d-129">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="7306d-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="7306d-130">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="7306d-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
