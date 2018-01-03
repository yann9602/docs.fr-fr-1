---
title: Utiliser la mise en cache dans UI Automation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 808ba16cbacfad2cc255ae40e2cbad3178350afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="9d723-102">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="9d723-102">Use Caching in UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="9d723-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="9d723-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9d723-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9d723-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9d723-105">Cette section montre comment implémenter la mise en cache des propriétés <xref:System.Windows.Automation.AutomationElement> et des modèles de contrôle.</span><span class="sxs-lookup"><span data-stu-id="9d723-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="9d723-106">Activer une requête de Cache</span><span class="sxs-lookup"><span data-stu-id="9d723-106">Activate a Cache Request</span></span>  
  
1.  <span data-ttu-id="9d723-107">Créez un <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9d723-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="9d723-108">Spécifiez les propriétés et les modèles à mettre en cache à l’aide de la méthode <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d723-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3.  <span data-ttu-id="9d723-109">Spécifiez la portée de la mise en cache en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="9d723-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4.  <span data-ttu-id="9d723-110">Spécifiez l’affichage de la sous-arborescence en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="9d723-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5.  <span data-ttu-id="9d723-111">Affectez à la propriété <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> la valeur <xref:System.Windows.Automation.AutomationElementMode.None> si vous souhaitez augmenter l’efficacité en ne récupérant pas de référence complète aux objets.</span><span class="sxs-lookup"><span data-stu-id="9d723-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="9d723-112">(Cela rend impossible la récupération des valeurs actuelles de ces objets.)</span><span class="sxs-lookup"><span data-stu-id="9d723-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6.  <span data-ttu-id="9d723-113">Activez la requête en utilisant <xref:System.Windows.Automation.CacheRequest.Activate%2A> dans un bloc `using` (`Using` dans [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="9d723-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span></span>  
  
 <span data-ttu-id="9d723-114">Après avoir obtenu des objets <xref:System.Windows.Automation.AutomationElement> ou vous être inscrit à des événements, désactivez la requête en utilisant <xref:System.Windows.Automation.CacheRequest.Pop%2A> (si <xref:System.Windows.Automation.CacheRequest.Push%2A> a été utilisé) ou en supprimant l’objet créé par <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d723-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="9d723-115">(Utilisez <xref:System.Windows.Automation.CacheRequest.Activate%2A> dans un bloc `using` (`Using` dans [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="9d723-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="9d723-116">Mettre en cache des propriétés AutomationElement</span><span class="sxs-lookup"><span data-stu-id="9d723-116">Cache AutomationElement Properties</span></span>  
  
1.  <span data-ttu-id="9d723-117">Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif.</span><span class="sxs-lookup"><span data-stu-id="9d723-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9d723-118">(Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="9d723-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="9d723-119">Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez une propriété de la propriété <xref:System.Windows.Automation.AutomationElement.Cached%2A> de l’ <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="9d723-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="9d723-120">Obtenir des modèles mis en cache et leurs propriétés</span><span class="sxs-lookup"><span data-stu-id="9d723-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1.  <span data-ttu-id="9d723-121">Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif.</span><span class="sxs-lookup"><span data-stu-id="9d723-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9d723-122">(Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="9d723-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="9d723-123">Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> pour récupérer un modèle mis en cache.</span><span class="sxs-lookup"><span data-stu-id="9d723-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3.  <span data-ttu-id="9d723-124">Récupérez les valeurs de propriété de la propriété `Cached` du modèle de contrôle.</span><span class="sxs-lookup"><span data-stu-id="9d723-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d723-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d723-125">Example</span></span>  
 <span data-ttu-id="9d723-126">L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Activate%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9d723-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="9d723-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="9d723-127">Example</span></span>  
 <span data-ttu-id="9d723-128">L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Push%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9d723-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="9d723-129">Excepté lorsque vous souhaitez imbriquer des requêtes de cache, il est préférable d’utiliser <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d723-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="9d723-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d723-130">See Also</span></span>  
 [<span data-ttu-id="9d723-131">Mise en cache dans les clients UI Automation</span><span class="sxs-lookup"><span data-stu-id="9d723-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
