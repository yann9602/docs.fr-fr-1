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
# <a name="garbage-collection-notifications"></a>Notifications de garbage collection
Il existe des situations dans lesquelles une garbage collection complet (autrement dit, une collection de génération 2) par le common language runtime peut nuire aux performances. Cela peut être particulièrement problématique avec les serveurs qui traitent de gros volumes de requêtes. Dans ce cas, un garbage collection long peut entraîner un délai d’expiration de la demande. Pour empêcher une collection complète qui se produisent pendant une période critique, vous pouvez être informé qu’un garbage collection complet approche et agir en conséquence pour rediriger la charge de travail vers une autre instance de serveur. Vous pouvez également induire vous-même une collection, sous réserve que l’instance de serveur actuelle n’a pas besoin de traiter les demandes.  
  
 Le <xref:System.GC.RegisterForFullGCNotification%2A> méthode inscrit pour une notification à déclencher lorsque le runtime détecte que le garbage collection complet est proche. À cette notification en deux parties : lorsque la garbage collection complet est imminent et lorsque le garbage collection complet est terminée.  
  
> [!WARNING]
>  Seul garbage collections de blocage générer des notifications. Lorsque le [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) élément de configuration est activé, les nettoyages en arrière-plan ne génère pas de notifications.  
  
 Pour déterminer lorsqu’une notification a été levée, utilisez la <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes. En général, vous utilisez ces méthodes dans un `while` boucle pour obtenir en permanence un <xref:System.GCNotificationStatus> énumération qui indique l’état de la notification. Si cette valeur est <xref:System.GCNotificationStatus.Succeeded>, vous pouvez procédez comme suit :  
  
-   En réponse à une notification obtenue avec la <xref:System.GC.WaitForFullGCApproach%2A> (méthode), vous pouvez rediriger la charge de travail et éventuellement induire vous-même une collection.  
  
-   En réponse à une notification obtenue avec la <xref:System.GC.WaitForFullGCComplete%2A> (méthode), vous pouvez rendre l’instance de serveur actuelle disponible pour traiter les demandes. Vous pouvez également collecter des informations. Par exemple, vous pouvez utiliser la <xref:System.GC.CollectionCount%2A> méthode pour enregistrer le nombre de collections.  
  
 Le <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes sont conçus pour fonctionner ensemble. À l’aide d’une sans l’autre peut produire des résultats indéterminés.  
  
## <a name="full-garbage-collection"></a>Un Garbage Collection complet  
 Le runtime génère un garbage collection complet lors d’une des situations suivantes est vraie :  
  
-   Suffisamment de mémoire a été promue dans la génération 2 pour entraîner la collection de génération 2 suivante.  
  
-   Suffisamment de mémoire a été promue dans le tas d’objets volumineux pour entraîner la collection de génération 2 suivante.  
  
-   Une collection de génération 1 est transmise à une collection de génération 2 en raison d’autres facteurs.  
  
 Les seuils que vous spécifiez dans le <xref:System.GC.RegisterForFullGCNotification%2A> méthode s’applique aux deux premiers scénarios. Toutefois, dans le premier scénario vous pas toujours recevront la notification en temps proportionnel aux valeurs de seuil que vous spécifiez pour deux raisons :  
  
-   Le runtime ne vérifie pas chaque allocation de petits objets (pour des raisons de performances).  
  
-   Uniquement la génération 1 collections promeuvent la mémoire dans la génération 2.  
  
 Le troisième scénario contribue également à l’incertitude lorsque vous recevez la notification. Bien que cela n’est pas une garantie, elle prouve à constituer un moyen utile pour atténuer les effets d’une garbage collection complet intempestif en redirigeant les requêtes pendant ce temps ou induire vous-même la collection lorsqu’il est mieux possible.  
  
## <a name="notification-threshold-parameters"></a>Paramètres de seuil de notification  
 Le <xref:System.GC.RegisterForFullGCNotification%2A> méthode possède deux paramètres pour spécifier les valeurs de seuil des objets de génération 2 et le tas d’objets volumineux. Lorsque ces valeurs sont remplies, une notification de garbage collection doit être déclenchée. Le tableau suivant décrit ces paramètres.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Un nombre compris entre 1 et 99 qui spécifie quand la notification doit être émise selon les objets promus dans la génération 2.|  
|`largeObjectHeapThreshold`|Un nombre compris entre 1 et 99 qui spécifie quand la notification doit être émise selon les objets qui sont alloués dans le tas d’objets volumineux.|  
  
 Si vous spécifiez une valeur trop élevée, il existe une forte probabilité que vous recevrez une notification, mais elle peut être trop long une période d’attente avant que le runtime déclenche une collection. Si vous induisez vous-même une collection, vous pouvez récupérer plus d’objets que serait récupérés si le runtime provoque la collection.  
  
 Si vous spécifiez une valeur qui est trop faible, le runtime peut entraîner la collection avant que vous avez suffisamment de temps pour être averti.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l’exemple suivant, un groupe de serveurs de service des demandes Web entrantes. Pour simuler la charge de travail de traitement des demandes, les tableaux d’octets sont ajoutés à un <xref:System.Collections.Generic.List%601> collection. Chaque serveur inscrit pour une notification de garbage collection et puis démarre un thread sur le `WaitForFullGCProc` méthode utilisateur pour surveiller en permanence la <xref:System.GCNotificationStatus> énumération retournée par le <xref:System.GC.WaitForFullGCApproach%2A> et le <xref:System.GC.WaitForFullGCComplete%2A> méthodes.  
  
 Le <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> méthodes appellent leurs méthodes utilisateur de gestion des événements respectives lorsqu’une notification est levée :  
  
-   `OnFullGCApproachNotify`  
  
     Cette méthode appelle la `RedirectRequests` méthode utilisateur, ce qui indique au serveur de file d’attente de demande pour interrompre l’envoi de demandes au serveur. Cela est simulé en définissant la variable de niveau classe `bAllocate` à `false` afin qu’aucun autre objet n’est alloués.  
  
     Ensuite, le `FinishExistingRequests` méthode utilisateur est appelée pour terminer le traitement des demandes en attente du serveur. Cela est simulé en désactivant le <xref:System.Collections.Generic.List%601> collection.  
  
     Enfin, un garbage collection ne soit induit car la charge de travail est faible.  
  
-   `OnFullGCCompleteNotify`  
  
     Cette méthode appelle la méthode utilisateur `AcceptRequests` pour reprendre l’acceptation des demandes, car le serveur n’est plus vulnérable à un garbage collection complet. Cette action est simulée en définissant le `bAllocate` variable `true` afin que les objets peuvent reprendre ajouté à la <xref:System.Collections.Generic.List%601> collection.  
  
 Le code suivant contient la `Main` méthode de l’exemple.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Le code suivant contient la `WaitForFullGCProc` méthode utilisateur, qui contient une boucle continue while pour vérifier les notifications de garbage collection.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Le code suivant contient la `OnFullGCApproachNotify` la méthode appelée à partir de la  
  
 Méthode `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Le code suivant contient la `OnFullGCApproachComplete` la méthode appelée à partir de la  
  
 Méthode `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Le code suivant contient les méthodes de l’utilisateur qui sont appelées à partir de la `OnFullGCApproachNotify` et `OnFullGCCompleteNotify` méthodes. Les méthodes de l’utilisateur redirigent les demandes, terminer les demandes existantes, puis reprennent les demandes après qu’un garbage collection s’est produite.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 L’exemple de code complet est la suivante :  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
