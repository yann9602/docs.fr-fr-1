---
title: "Garbage Collection Notifications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "garbage collection, notifications"
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Garbage Collection Notifications
Dans certains cas, un garbage collection complet \(étant une plus une collection de génération 2\) effectué par le common language runtime peut gêner les performances.  Cela peut être particulièrement problématique avec les serveurs qui traitent d'importants volumes de requêtes. Dans ce cas, un garbage collection long peut entraîner une expiration de la requête.  Pour empêcher la réalisation d'une collection complète pendant une période critique, vous pouvez être notifié qu'un garbage collection complet approche, puis prendre les mesures qui s'imposent pour rediriger la charge de travail vers une autre instance de serveur.  Vous pouvez également induire vous\-même une collection, tant que l'instance de serveur actuelle n'a pas besoin de traiter des demandes.  
  
 La méthode <xref:System.GC.RegisterForFullGCNotification%2A> s'inscrit à une notification devant être levée lorsque l'exécution prévoit qu'un nettoyage de la mémoire complet est imminent.  Cette notification est composée de deux parties : lorsque le garbage collection complet est imminent et lorsque le garbage collection complet est terminé.  
  
> [!WARNING]
>  Seuls les garbages collection de blocage déclenchent des notifications.  Lorsque l'élément de configuration de [\<gcConcurrent\>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) est activé, les garbages collection d'arrière\-plan ne déclenche pas de notification.  
  
 Pour déterminer à quel moment une notification a été levée, utilisez les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>.  Vous pouvez généralement utiliser ces méthodes dans une boucle `while` pour obtenir sans cesse une énumération <xref:System.GCNotificationStatus> qui affiche l'état de la notification.  Si cette valeur est <xref:System.GCNotificationStatus>, vous pouvez effectuer les opérations suivantes :  
  
-   En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCApproach%2A>, vous pouvez rediriger la charge de travail et éventuellement induire vous\-même une collection.  
  
-   En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCComplete%2A>, vous pouvez obtenir de l'instance de serveur actuelle qu'elle traite encore des demandes.  Vous pouvez également rassembler des informations.  Par exemple, vous pouvez utiliser la méthode <xref:System.GC.CollectionCount%2A> pour enregistrer le nombre de collections.  
  
 Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> sont conçues pour fonctionner ensemble.  L'utilisation de l'une sans l'autre peut entraîner des résultats indéterminés.  
  
## Garbage collection complet  
 L'exécution entraîne un garbage collection complet si l'un des scénarios suivants est vrai :  
  
-   suffisamment de mémoire a été promue dans la génération 2 pour entraîner la collection de génération 2 suivante ;  
  
-   suffisamment de mémoire a été promue dans le tas d'objets volumineux pour entraîner la collection de génération 2 suivante ;  
  
-   une collection de génération 1 est transmise à une collection de génération 2 en raison d'autres facteurs.  
  
 Les seuils que vous avez spécifié dans la méthode <xref:System.GC.RegisterForFullGCNotification%2A> s'appliquent aux deux premiers scénarios.  Toutefois, pour deux raisons, lors du premier scénario, vous ne recevrez pas toujours la notification au bon moment selon les valeurs de seuil spécifiées :  
  
-   l'exécution ne vérifie pas toutes les allocations d'objet \(pour des raisons de performance\) ;  
  
-   seules les collections de génération 1 promeuvent la mémoire dans la génération 2.  
  
 Le troisième scénario alimente également l'incertitude quant au moment de réception de la notification.  Bien qu'elle ne soit pas garantie, cette méthode est un bon moyen d'atténuer les effets d'un garbage collection complet intempestif, en vous permettant de rediriger les demandes ou d'induire vous\-même la collection à un moment plus opportun.  
  
## Paramètres du seuil de notification  
 La méthode <xref:System.GC.RegisterForFullGCNotification%2A> comporte deux paramètres pour spécifier les valeurs de seuil des objets de la génération 2 et du tas d'objets volumineux.  Lorsque ces valeurs sont atteintes, une notification de garbage collection doit être levée.  Le tableau suivant décrit ces paramètres.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Un nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être levée selon les objets promus dans la génération 2.|  
|`largeObjectHeapThreshold`|Un nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être levée selon les objets affectés dans le tas d'objets volumineux.|  
  
 Si vous spécifiez une valeur trop élevée, il y a de grandes chances que vous receviez une notification. Cependant, la période peut être trop longue avant que l'exécution n'entraîne une collection.  Si vous induisez vous\-même une collection, il est possible que récupériez plus d'objets que si l'exécution entrainait la collection.  
  
 Si vous spécifiez une valeur trop basse, l'exécution peut entraîner la collection avant que la notification ait été envoyée.  
  
## Exemple  
  
### Description  
 Dans l'exemple suivant, un groupe de serveurs traite les demandes Web entrantes.  Pour simuler la charge de travail induite par le traitement des demandes, des tableaux d'octets sont ajoutés à une collection <xref:System.Collections.Generic.List%601>.  Chaque serveur s'inscrit à une notification de garbage collection, puis démarre un thread sur la méthode utilisateur `WaitForFullGCProc` pour surveiller continuellement l'énumération <xref:System.GCNotificationStatus> retournée par les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>.  
  
 Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> appellent leurs méthodes utilisateur de gestion des événements respectives lorsqu'une notification est levée:  
  
-   `OnFullGCApproachNotify`  
  
     Cette méthode appelle la méthode utilisateur `RedirectRequests` qui indique au serveur de mise en file d'attente des demandes d'interrompre l'envoi de demandes au serveur.  On peut la simuler en affectant la valeur `false` à la variable de niveau de la classe `bAllocate` afin que plus aucun objet ne soit affecté.  
  
     La méthode utilisateur `FinishExistingRequests` est ensuite appelée pour terminer le traitement des demandes en attente du serveur.  On peut le simuler en effaçant la collection <xref:System.Collections.Generic.List%601>.  
  
     Un garbage collection est ensuite induit car la charge de travail n'est pas trop importante.  
  
-   `OnFullGCCompleteNotify`  
  
     Cette méthode appelle la méthode utilisateur `AcceptRequests` pour reprendre l'acceptation des demandes car le serveur ne risque plus de garbage collection complet.  On peut simuler cette opération en affectant la valeur `true` à la variable `bAllocate` afin que les objets soient de nouveau ajoutés à la collection <xref:System.Collections.Generic.List%601>.  
  
 Le code suivant contient la méthode `Main` de l'exemple.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Le code suivant contient la méthode utilisateur `WaitForFullGCProc` qui comprend une boucle continue while permettant de vérifier les notifications de garbage collection.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Le code suivant contient la méthode `OnFullGCApproachNotify` comme elle est appelée depuis la  
  
 Méthode `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Le code suivant contient la méthode `OnFullGCApproachComplete` comme elle est appelée depuis la  
  
 Méthode `WaitForFullGCProc`.  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Le code suivant contient les méthodes utilisateur appelées depuis les méthodes `OnFullGCApproachNotify` et `OnFullGCCompleteNotify`.  Les méthodes utilisateur redirigent les demandes, terminent le traitement des demandes existantes, puis reprennent les demandes après l'exécution d'un garbage collection complet.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 Ci\-dessous, l'exemple de code complet :  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## Voir aussi  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)