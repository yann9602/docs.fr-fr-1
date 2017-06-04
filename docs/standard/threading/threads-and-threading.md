---
title: "Threads and Threading | Microsoft Docs"
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
  - "multiple threads"
  - "threading [.NET Framework]"
  - "threading [.NET Framework], multiple threads"
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Threads and Threading
Les systèmes d'exploitation utilisent des processus pour séparer les différentes applications qu'ils exécutent.  Les threads sont l'unité de base à laquelle un système d'exploitation alloue du temps processeur, et plusieurs threads peuvent exécuter du code à l'intérieur de ce processus.  Chaque thread gère des gestionnaires d'exceptions, une priorité de planification et un jeu de structures que le système utilise pour enregistrer le contexte du thread jusqu'à ce qu'il soit planifié.  Le contexte du thread comprend toutes les informations dont le thread a besoin pour reprendre l'exécution de façon transparente, y compris le jeu des registres de CPU et de pile du thread dans l'espace d'adressage du processus hôte du thread.  
  
 Le .NET Framework subdivise davantage un processus de système d'exploitation en sous\-processus managés, légers connus sous le nom de domaines d'application, représentés par <xref:System.AppDomain?displayProperty=fullName>.  Un ou plusieurs threads managés \(représentés par <xref:System.Threading.Thread?displayProperty=fullName>\) peuvent s'exécuter dans un ou plusieurs domaines d'application au sein du même processus managé.  Même si chaque domaine d'application commence avec un thread unique, le code dans ce domaine d'application peut créer des domaines d'application supplémentaires et des threads supplémentaires.  Par conséquent, un thread managé peut aller et venir librement entre des domaines d'application à l'intérieur du même processus managé ; vous pouvez n'avoir qu'un seul thread se déplaçant parmi plusieurs domaines d'application.  
  
 Un système d'exploitation qui prend en charge le multitâche préemptif crée un effet d'exécution simultanée de plusieurs threads issus de plusieurs processus.  Cette opération est possible en répartissant le temps processus entre les threads qui en ont besoin, allouant une tranche de temps processeur à chaque thread l'un après l'autre.  Le thread en cours d'exécution est interrompu lorsque sa tranche de temps est écoulée et lorsqu'un autre thread reprend l'exécution.  Lorsque le système passe d'un thread à l'autre, il enregistre le contexte thread du thread préempté et recharge le contexte enregistré du thread suivant dans la file d'attente des threads.  
  
 La durée de la tranche de temps dépend du système d'exploitation et du processeur.  Comme chaque tranche de temps est courte, plusieurs threads semblent s'exécuter en même temps, même s'il n'y a qu'un seul processeur.  C'est précisément le cas sur les systèmes multiprocesseurs où les threads exécutables sont distribués entre les processeurs disponibles.  
  
## Quand utiliser plusieurs threads  
 Les logiciels qui nécessitent une interaction de l'utilisateur doivent réagir aux activités de l'utilisateur aussi rapidement que possible pour fournir à celui\-ci une interaction totale.  Cependant, ces logiciels doivent en même temps effectuer les calculs nécessaires pour présenter les données à l'utilisateur aussi rapidement que possible.  Si votre application n'utilise qu'un seul thread d'exécution, vous pouvez associer la [programmation asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) au [.NET Framework Remoting](http://msdn.microsoft.com/fr-fr/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) ou aux [services Web XML](http://msdn.microsoft.com/fr-fr/1e64af78-d705-4384-b08d-591a45f4379c) créés à l'aide d'ASP.NET pour utiliser le temps de traitement d'autres ordinateurs en plus du vôtre afin d'accroître la réactivité par rapport à l'utilisateur et réduire le temps de traitement des données de votre application.  Si votre travail d'entrée\/sortie est intense, vous pouvez également utiliser les ports de terminaison d'E\/S pour accroître la réactivité de votre application.  
  
### Avantages de plusieurs threads  
 Cependant, l'utilisation de plusieurs threads est la technique disponible la plus efficace pour accroître la réactivité par rapport à l'utilisateur et traiter d'une manière presque simultanée les données nécessaires à l'accomplissement des tâches.  Sur un ordinateur équipé d'un processeur, plusieurs threads peuvent créer cet effet, tirant profit de courtes périodes de temps entre les événements utilisateur pour traiter les données en arrière\-plan.  Par exemple, un utilisateur peut éditer une feuille de calcul, tandis qu'un autre thread recalcule d'autres parties de la feuille de calcul au sein de la même application.  
  
 Sans modification, la même application augmenterait très nettement la satisfaction de l'utilisateur si elle fonctionnait sur un ordinateur multiprocesseur.  Votre domaine d'application unique pourrait utiliser plusieurs threads pour accomplir les tâches suivantes :  
  
-   Communiquer sur un réseau à un serveur Web ou une base de données.  
  
-   Effectuer des opérations qui prennent beaucoup de temps.  
  
-   Faire la distinction entre des tâches de priorité diverse.  Par exemple, un thread de priorité supérieure gère les tâches critiques, et un thread de priorité inférieure effectue d'autres tâches.  
  
-   Permettre à l'interface utilisateur de garder son répondant tout en allouant du temps aux tâches en arrière\-plan.  
  
### Désavantages de plusieurs threads  
 Il est recommandé d'utiliser aussi peu de threads que possible pour ainsi minimiser l'utilisation des ressources du système d'exploitation et améliorer les performances.  Les exigences en matière de ressources et les conflits potentiels du threading sont à prendre en compte lors de la conception de votre application.  Les exigences en matière de ressources sont les suivantes :  
  
-   Le système consomme de la mémoire pour les informations de contexte dont les processus, les objets **AppDomain** et les threads ont besoin.  Par conséquent, le nombre de processus, d'objets **AppDomain** et de threads qui peuvent être créés est limité par la mémoire disponible.  
  
-   Assurer le suivi d'un grand nombre de threads consomme une portion significative de temps processeur.  S'il y a trop de threads, la plupart ne feront pas beaucoup de progrès.  Si la plupart des threads en cours sont dans un processus, les threads des autres processus sont planifiés moins fréquemment.  
  
-   Le contrôle de l'exécution du code contenant de nombreux threads est complexe et peut être la source de nombreuses bogues.  
  
-   La destruction de threads implique une connaissance des conséquences qui en résultent et le traitement de ces problèmes.  
  
 Fournir un accès partagé à des ressources peut créer des conflits.  Afin d'éviter ces conflits, vous devez synchroniser ou contrôler l'accès aux ressources partagées.  Si cette synchronisation fait défaut \(dans le même ou dans différents domaines d'application\), des problèmes tels que les interblocages \(deux threads cessent de répondre, l'une attendant que l'autre se termine\) et les conditions de concurrence critique \(anomalie de résultat provoquée par une dépendance critique inattendue à l'égard de la synchronisation de deux événements\).  Le système fournit des objets de synchronisation qui peuvent être utilisés pour coordonner le partage de ressources parmi plusieurs threads.  La réduction du nombre de threads simplifie la synchronisation des ressources.  
  
 Les ressources qui nécessitent une synchronisation comprennent :  
  
-   Les ressources du système \(comme les ports de communication\).  
  
-   Les ressources partagées par plusieurs processus \(comme les handles de fichiers\).  
  
-   Les ressources d'un domaine d'application unique \(tel que des champs d'instance, statiques et globaux\) accessibles par plusieurs threads.  
  
### Threading et design d'application  
 En général, l'utilisation de la classe <xref:System.Threading.ThreadPool> constitue la manière la plus simple pour gérer plusieurs threads pour les tâches relativement courtes qui ne bloquent pas d'autres threads et lorsque vous ne prévoyez aucune planification particulière des tâches.  Cependant, il existe plusieurs raisons pour créer vos propres threads :  
  
-   Si vous avez besoin qu'une tâche suive une priorité particulière.  
  
-   Si vous avez une tâche qui risque de prendre longtemps \(bloquant ainsi d'autres tâches\).  
  
-   Si vous avez besoin de placer des threads dans un thread cloisonné \(STA, Single\-Threaded Apartment\) \(tous les threads **ThreadPool** sont dans le MTA \(Multithreaded Apartment\)\).  
  
-   Si vous avez besoin d'une identité stable associée au thread.  Par exemple, vous devez utiliser un thread dédié pour abandonner ce thread, l'interrompre ou l'identifier par son nom.  
  
-   Si vous devez exécuter des threads d'arrière\-plan qui interagissent avec l'interface utilisateur, le .NET Framework version 2.0 fournit un composant <xref:System.ComponentModel.BackgroundWorker> qui communique à l'aide d'événements, avec un marshaling inter\-threads vers le thread d'interface utilisateur.  
  
### Threads et exceptions  
 Gérez des exceptions dans les threads.  Les exceptions non gérées dans les threads, même des threads d'arrière\-plan, arrêtent généralement le processus.  Il existe trois exceptions à cette règle :  
  
-   Un <xref:System.Threading.ThreadAbortException> est levé dans un thread en raison d'un appel à <xref:System.Threading.Thread.Abort%2A>.  
  
-   Un <xref:System.AppDomainUnloadedException> est levé dans un thread, car le domaine d'application est en cours de déchargement.  
  
-   Le Common Language Runtime ou un processus hôte met fin au thread.  
  
 Pour plus d'informations, consultez [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Dans les versions 1.0 et 1.1 du .NET Framework, le Common Language Runtime intercepte en mode silencieux certaines exceptions dans les threads du pool de threads.  Cela peut endommager l'état de l'application et éventuellement provoquer le blocage des applications, ce qui peut être très difficile à déboguer.  
  
## Voir aussi  
 <xref:System.Threading.ThreadPool>   
 <xref:System.ComponentModel.BackgroundWorker>   
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)   
 [The Managed Thread Pool](../../../docs/standard/threading/the-managed-thread-pool.md)