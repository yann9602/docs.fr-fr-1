---
title: Threads et threading
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b57cac34009e13c27c6d34a0ab402f9ecbe08305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="threads-and-threading"></a>Threads et threading
Systèmes d’exploitation permet de séparer les différentes applications qu’ils exécutent des processus. Les threads sont l’unité de base à laquelle un système d’exploitation alloue du temps processeur et à plusieurs threads peuvent exécuter du code à l’intérieur de ce processus. Chaque thread maintient des gestionnaires d’exceptions, une priorité de planification et un ensemble de structures, que le système utilise pour enregistrer le contexte du thread jusqu'à ce qu’elle est planifiée. Le contexte de thread inclut toutes les informations que le thread doit reprendre sans interruption de l’exécution, notamment l’ensemble du thread de registres de l’UC et de la pile, dans l’espace d’adressage de processus de l’hôte du thread.  
  
 Le .NET Framework subdivise davantage un processus de système d’exploitation en légers sous-processus gérés, appelés domaines d’application, représentés par <xref:System.AppDomain?displayProperty=nameWithType>. Un ou plusieurs threads managés (représentée par <xref:System.Threading.Thread?displayProperty=nameWithType>) peuvent s’exécuter dans un ou plusieurs des domaines d’application au sein du même processus managé. Bien que chaque domaine d’application est démarrée avec un thread unique, le code dans ce domaine d’application peut créer des domaines d’application supplémentaires et des threads supplémentaires. Le résultat est qu’un thread managé peut se déplacer librement entre domaines d’application à l’intérieur du même processus managé ; Vous pouvez avoir qu’un seul thread déplacement entre plusieurs domaines d’application.  
  
 Un système d’exploitation qui prend en charge les travaux multitâches préemptifs crée l’effet de l’exécution simultanée de plusieurs threads à partir de plusieurs processus. Cette opération est possible répartissant le temps processeur disponible entre les threads qui en ont besoin, allouant une tranche de temps processeur pour chaque thread un après l’autre. Le thread en cours d’exécution est suspendu lorsque sa durée de tranche est écoulé et un autre thread reprend l’exécution. Lorsque le système passe à partir d’un thread à un autre, il enregistre le contexte du thread du thread préempté et recharge le contexte enregistré du thread suivant dans la file d’attente du thread.  
  
 La longueur de la tranche de temps dépend du système d’exploitation et le processeur. Étant donné que chaque tranche de temps est petite, plusieurs threads semblent s’exécuter en même temps, même s’il existe un seul processeur. Il s’agit en fait le cas sur les systèmes multiprocesseurs, où les threads exécutables sont distribués entre les processeurs disponibles.  
  
## <a name="when-to-use-multiple-threads"></a>Quand utiliser plusieurs Threads  
 Logiciel qui nécessite l’intervention de l’utilisateur doit réagir aussi rapidement que possible pour fournir une expérience utilisateur riche pour les activités de l’utilisateur. En même temps, cependant, il doit effectuer les calculs nécessaires pour présenter les données à l’utilisateur aussi rapidement que possible. Si votre application utilise un seul thread d’exécution, vous pouvez combiner [programmation asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) avec[.NET Framework remoting](http://msdn.microsoft.com/en-us/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) ou [des services Web XML](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c) créé à l’aide d’ASP .NET pour utiliser le temps de traitement d’autres ordinateurs en plus de votre propre pour augmenter la réactivité de l’utilisateur et à réduire le temps de traitement des données de votre application. Si vous effectuez des opérations d’entrée/sortie, vous pouvez également utiliser des ports de terminaison d’e/s pour augmenter la réactivité de votre application.  
  
### <a name="advantages-of-multiple-threads"></a>Avantages de plusieurs Threads  
 À l’aide de plusieurs threads, toutefois, est la technique la plus puissante disponible pour augmenter la réactivité de l’utilisateur et de traiter les données nécessaires pour effectuer le travail en même temps presque. Sur un ordinateur avec un seul processeur, plusieurs threads peuvent créer cet effet, en tirant profit de courtes périodes de temps entre les événements utilisateur pour traiter les données en arrière-plan. Par exemple, un utilisateur peut modifier une feuille de calcul lors d’un autre thread recalcule d’autres parties de la feuille de calcul dans la même application.  
  
 Sans modification, la même application augmenterait la satisfaction utilisateur lorsque vous exécutez sur un ordinateur avec plusieurs processeurs. Votre domaine d’application unique pourrait utiliser plusieurs threads pour accomplir les tâches suivantes :  
  
-   Communiquent via un réseau, un serveur Web et une base de données.  
  
-   Effectuer des opérations qui prennent beaucoup de temps.  
  
-   Différencier les tâches de priorité différents. Par exemple, un thread de priorité supérieure gère les tâches en temps critique, et un thread de priorité inférieure effectue d’autres tâches.  
  
-   Autoriser l’interface utilisateur de rester réactive, lors de l’allocation de temps aux tâches en arrière-plan.  
  
### <a name="disadvantages-of-multiple-threads"></a>Inconvénients de plusieurs Threads  
 Il est recommandé d’utiliser aussi peu de threads que possible, réduisant ainsi l’utilisation des ressources du système d’exploitation et améliorer les performances. Threading possède également les besoins en ressources et les conflits potentiels à prendre en considération lorsque vous concevez votre application. Les besoins en ressources sont les suivantes :  
  
-   Le système utilise la mémoire pour les informations de contexte requises par le processus, **AppDomain** objets et les threads. Par conséquent, le nombre de processus, **AppDomain** objets et les threads qui peuvent être créés est limité par la mémoire disponible.  
  
-   Le suivi d’un grand nombre de threads consomme un temps processeur important. S’il y a trop de threads, la plupart d'entre elles n’apporte un progrès important. Si la plupart des threads en cours est dans un processus, threads dans d’autres processus sont planifiés moins fréquemment.  
  
-   Contrôle de l’exécution de code avec un grand nombre de threads est complexe et peut être une source de nombreux bogues.  
  
-   Détruire des threads nécessite le fait de savoir ce qui peut se produire et le traitement de ces problèmes.  
  
 Fournir un accès partagé aux ressources peut créer des conflits. Pour éviter les conflits, vous devez synchroniser ou contrôler l’accès aux ressources partagées. Échec pour synchroniser l’accès correctement (dans les même ou différents domaines d’application) peut entraîner des problèmes tels que des blocages (deux threads cesser de répondre attendant que l’autre se termine) et les conditions de concurrence critique (anomalie de résultat se produit en raison un inattendue critiques dépendance de la synchronisation de deux événements). Le système fournit des objets de synchronisation qui peuvent être utilisés pour coordonner le partage de ressources entre plusieurs threads. Réduction du nombre de threads facilite la synchronisation des ressources.  
  
 Les ressources qui nécessitent une synchronisation sont les suivantes :  
  
-   Ressources système (telles que les ports de communication).  
  
-   Ressources partagées par plusieurs processus (par exemple, les handles de fichiers).  
  
-   Les ressources d’un seul domaine d’application (tels que global, statique et les champs d’instance) accessibles par plusieurs threads.  
  
### <a name="threading-and-application-design"></a>Conception de Threading et de l’Application  
 En général, à l’aide de la <xref:System.Threading.ThreadPool> classe est le moyen le plus simple pour gérer plusieurs threads pour les tâches relativement courtes qui ne bloquent pas les autres threads et lorsque vous ne prévoyez aucune planification particulière des tâches. Toutefois, il existe plusieurs raisons pour créer vos propres threads :  
  
-   Si vous avez besoin d’une tâche pour avoir une priorité particulière.  
  
-   Si vous avez une tâche qui peut exécuter un certain temps (et par conséquent bloque les autres tâches).  
  
-   Si vous devez placer des threads dans un thread unique cloisonné (tous les **ThreadPool** threads se trouvent dans le multithread cloisonné).  
  
-   Si vous avez besoin d’une identité stable associée au thread. Par exemple, vous devez utiliser un thread dédié pour abandonner ce thread, suspendre ou identifier par son nom.  
  
-   Si vous avez besoin exécuter des threads d’arrière-plan qui interagissent avec l’interface utilisateur, le .NET Framework version 2.0 fournit un <xref:System.ComponentModel.BackgroundWorker> composant qui communique à l’aide d’événements, avec un marshaling inter-threads vers le thread d’interface utilisateur.  
  
### <a name="threading-and-exceptions"></a>Thread et des Exceptions  
 Gérez des exceptions dans les threads. En règle générale, les exceptions non gérées dans les threads, les threads d’arrière-plan même terminer le processus. Il existe trois exceptions à cette règle :  
  
-   A <xref:System.Threading.ThreadAbortException> est levée dans un thread car <xref:System.Threading.Thread.Abort%2A> a été appelée.  
  
-   Un <xref:System.AppDomainUnloadedException> est levée dans un thread, car le domaine d’application est en cours de déchargement.  
  
-   Le common language runtime ou un processus hôte met fin au thread.  
  
 Pour plus d’informations, consultez [Exceptions dans les Threads managés](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Dans les versions 1.0 et 1.1 du .NET Framework, le common language runtime intercepte en mode silencieux certaines exceptions, par exemple dans les threads du pool. Cela peut endommager l’état de l’application et éventuellement provoquer le blocage, des applications qui peuvent être très difficiles à déboguer.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Synchronisation des données pour le multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Pool de threads managés](../../../docs/standard/threading/the-managed-thread-pool.md)
