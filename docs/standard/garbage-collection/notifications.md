---
title: Notifications de garbage collection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="66101-102">Notifications de garbage collection</span><span class="sxs-lookup"><span data-stu-id="66101-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="66101-103">Il existe des situations dans lesquelles une garbage collection complet (autrement dit, une collection de génération 2) par le common language runtime peut nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="66101-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="66101-104">Cela peut être particulièrement problématique avec les serveurs qui traitent de gros volumes de requêtes. Dans ce cas, un garbage collection long peut entraîner un délai d’expiration de la demande. Pour empêcher une collection complète qui se produisent pendant une période critique, vous pouvez être informé qu’un garbage collection complet approche et agir en conséquence pour rediriger la charge de travail vers une autre instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="66101-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="66101-105">Vous pouvez également induire vous-même une collection, sous réserve que l’instance de serveur actuelle n’a pas besoin de traiter les demandes.</span><span class="sxs-lookup"><span data-stu-id="66101-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="66101-106">Le <xref:System.GC.RegisterForFullGCNotification%2A> méthode inscrit pour une notification à déclencher lorsque le runtime détecte que le garbage collection complet est proche.</span><span class="sxs-lookup"><span data-stu-id="66101-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="66101-107">À cette notification en deux parties : lorsque la garbage collection complet est imminent et lorsque le garbage collection complet est terminée.</span><span class="sxs-lookup"><span data-stu-id="66101-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="66101-108">Seul garbage collections de blocage générer des notifications.</span><span class="sxs-lookup"><span data-stu-id="66101-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="66101-109">Lorsque le [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) élément de configuration est activé, les nettoyages en arrière-plan ne génère pas de notifications.</span><span class="sxs-lookup"><span data-stu-id="66101-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="66101-110">Pour déterminer lorsqu’une notification a été levée, utilisez la <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="66101-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="66101-111">En général, vous utilisez ces méthodes dans un `while` boucle pour obtenir en permanence un <xref:System.GCNotificationStatus> énumération qui indique l’état de la notification.</span><span class="sxs-lookup"><span data-stu-id="66101-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="66101-112">Si cette valeur est <xref:System.GCNotificationStatus.Succeeded>, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="66101-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="66101-113">En réponse à une notification obtenue avec la <xref:System.GC.WaitForFullGCApproach%2A> (méthode), vous pouvez rediriger la charge de travail et éventuellement induire vous-même une collection.</span><span class="sxs-lookup"><span data-stu-id="66101-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="66101-114">En réponse à une notification obtenue avec la <xref:System.GC.WaitForFullGCComplete%2A> (méthode), vous pouvez rendre l’instance de serveur actuelle disponible pour traiter les demandes.</span><span class="sxs-lookup"><span data-stu-id="66101-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="66101-115">Vous pouvez également collecter des informations.</span><span class="sxs-lookup"><span data-stu-id="66101-115">You can also gather information.</span></span> <span data-ttu-id="66101-116">Par exemple, vous pouvez utiliser la <xref:System.GC.CollectionCount%2A> méthode pour enregistrer le nombre de collections.</span><span class="sxs-lookup"><span data-stu-id="66101-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="66101-117">Le <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes sont conçus pour fonctionner ensemble.</span><span class="sxs-lookup"><span data-stu-id="66101-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="66101-118">À l’aide d’une sans l’autre peut produire des résultats indéterminés.</span><span class="sxs-lookup"><span data-stu-id="66101-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="66101-119">Un Garbage Collection complet</span><span class="sxs-lookup"><span data-stu-id="66101-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="66101-120">Le runtime génère un garbage collection complet lors d’une des situations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="66101-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="66101-121">Suffisamment de mémoire a été promue dans la génération 2 pour entraîner la collection de génération 2 suivante.</span><span class="sxs-lookup"><span data-stu-id="66101-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="66101-122">Suffisamment de mémoire a été promue dans le tas d’objets volumineux pour entraîner la collection de génération 2 suivante.</span><span class="sxs-lookup"><span data-stu-id="66101-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="66101-123">Une collection de génération 1 est transmise à une collection de génération 2 en raison d’autres facteurs.</span><span class="sxs-lookup"><span data-stu-id="66101-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="66101-124">Les seuils que vous spécifiez dans le <xref:System.GC.RegisterForFullGCNotification%2A> méthode s’applique aux deux premiers scénarios.</span><span class="sxs-lookup"><span data-stu-id="66101-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="66101-125">Toutefois, dans le premier scénario vous pas toujours recevront la notification en temps proportionnel aux valeurs de seuil que vous spécifiez pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="66101-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="66101-126">Le runtime ne vérifie pas chaque allocation de petits objets (pour des raisons de performances).</span><span class="sxs-lookup"><span data-stu-id="66101-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="66101-127">Uniquement la génération 1 collections promeuvent la mémoire dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="66101-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="66101-128">Le troisième scénario contribue également à l’incertitude lorsque vous recevez la notification.</span><span class="sxs-lookup"><span data-stu-id="66101-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="66101-129">Bien que cela n’est pas une garantie, elle prouve à constituer un moyen utile pour atténuer les effets d’une garbage collection complet intempestif en redirigeant les requêtes pendant ce temps ou induire vous-même la collection lorsqu’il est mieux possible.</span><span class="sxs-lookup"><span data-stu-id="66101-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="66101-130">Paramètres de seuil de notification</span><span class="sxs-lookup"><span data-stu-id="66101-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="66101-131">Le <xref:System.GC.RegisterForFullGCNotification%2A> méthode possède deux paramètres pour spécifier les valeurs de seuil des objets de génération 2 et le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="66101-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="66101-132">Lorsque ces valeurs sont remplies, une notification de garbage collection doit être déclenchée.</span><span class="sxs-lookup"><span data-stu-id="66101-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="66101-133">Le tableau suivant décrit ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="66101-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="66101-134">Paramètre</span><span class="sxs-lookup"><span data-stu-id="66101-134">Parameter</span></span>|<span data-ttu-id="66101-135">Description</span><span class="sxs-lookup"><span data-stu-id="66101-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="66101-136">Un nombre compris entre 1 et 99 qui spécifie quand la notification doit être émise selon les objets promus dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="66101-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="66101-137">Un nombre compris entre 1 et 99 qui spécifie quand la notification doit être émise selon les objets qui sont alloués dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="66101-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="66101-138">Si vous spécifiez une valeur trop élevée, il existe une forte probabilité que vous recevrez une notification, mais elle peut être trop long une période d’attente avant que le runtime déclenche une collection.</span><span class="sxs-lookup"><span data-stu-id="66101-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="66101-139">Si vous induisez vous-même une collection, vous pouvez récupérer plus d’objets que serait récupérés si le runtime provoque la collection.</span><span class="sxs-lookup"><span data-stu-id="66101-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="66101-140">Si vous spécifiez une valeur qui est trop faible, le runtime peut entraîner la collection avant que vous avez suffisamment de temps pour être averti.</span><span class="sxs-lookup"><span data-stu-id="66101-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66101-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="66101-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="66101-142">Description</span><span class="sxs-lookup"><span data-stu-id="66101-142">Description</span></span>  
 <span data-ttu-id="66101-143">Dans l’exemple suivant, un groupe de serveurs de service des demandes Web entrantes.</span><span class="sxs-lookup"><span data-stu-id="66101-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="66101-144">Pour simuler la charge de travail de traitement des demandes, les tableaux d’octets sont ajoutés à un <xref:System.Collections.Generic.List%601> collection.</span><span class="sxs-lookup"><span data-stu-id="66101-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="66101-145">Chaque serveur inscrit pour une notification de garbage collection et puis démarre un thread sur le `WaitForFullGCProc` méthode utilisateur pour surveiller en permanence la <xref:System.GCNotificationStatus> énumération retournée par le <xref:System.GC.WaitForFullGCApproach%2A> et le <xref:System.GC.WaitForFullGCComplete%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="66101-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="66101-146">Le <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes appellent leurs méthodes utilisateur de gestion des événements respectives lorsqu’une notification est levée :</span><span class="sxs-lookup"><span data-stu-id="66101-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="66101-147">Cette méthode appelle la `RedirectRequests` méthode utilisateur, ce qui indique au serveur de file d’attente de demande pour interrompre l’envoi de demandes au serveur.</span><span class="sxs-lookup"><span data-stu-id="66101-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="66101-148">Cela est simulé en définissant la variable de niveau classe `bAllocate` à `false` afin qu’aucun autre objet n’est alloués.</span><span class="sxs-lookup"><span data-stu-id="66101-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="66101-149">Ensuite, le `FinishExistingRequests` méthode utilisateur est appelée pour terminer le traitement des demandes en attente du serveur.</span><span class="sxs-lookup"><span data-stu-id="66101-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="66101-150">Cela est simulé en désactivant le <xref:System.Collections.Generic.List%601> collection.</span><span class="sxs-lookup"><span data-stu-id="66101-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="66101-151">Enfin, un garbage collection ne soit induit car la charge de travail est faible.</span><span class="sxs-lookup"><span data-stu-id="66101-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="66101-152">Cette méthode appelle la méthode utilisateur `AcceptRequests` pour reprendre l’acceptation des demandes, car le serveur n’est plus vulnérable à un garbage collection complet.</span><span class="sxs-lookup"><span data-stu-id="66101-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="66101-153">Cette action est simulée en définissant le `bAllocate` variable `true` afin que les objets peuvent reprendre ajouté à la <xref:System.Collections.Generic.List%601> collection.</span><span class="sxs-lookup"><span data-stu-id="66101-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="66101-154">Le code suivant contient la `Main` méthode de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="66101-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="66101-155">Le code suivant contient la `WaitForFullGCProc` méthode utilisateur, qui contient une boucle continue while pour vérifier les notifications de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="66101-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="66101-156">Le code suivant contient la `OnFullGCApproachNotify` la méthode appelée à partir de la</span><span class="sxs-lookup"><span data-stu-id="66101-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="66101-157">Méthode `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="66101-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="66101-158">Le code suivant contient la `OnFullGCApproachComplete` la méthode appelée à partir de la</span><span class="sxs-lookup"><span data-stu-id="66101-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="66101-159">Méthode `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="66101-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="66101-160">Le code suivant contient les méthodes de l’utilisateur qui sont appelées à partir de la `OnFullGCApproachNotify` et `OnFullGCCompleteNotify` méthodes.</span><span class="sxs-lookup"><span data-stu-id="66101-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="66101-161">Les méthodes de l’utilisateur redirigent les demandes, terminer les demandes existantes, puis reprennent les demandes après qu’un garbage collection s’est produite.</span><span class="sxs-lookup"><span data-stu-id="66101-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="66101-162">L’exemple de code complet est la suivante :</span><span class="sxs-lookup"><span data-stu-id="66101-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="66101-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66101-163">See Also</span></span>  
 [<span data-ttu-id="66101-164">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="66101-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
