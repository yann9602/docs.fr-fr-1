---
title: "Managed Threading | Microsoft Docs"
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
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading
Que vous développiez pour des ordinateurs équipés d'un ou de plusieurs processeurs, vous voulez que vos applications fournissent l'interaction la plus efficace avec l'utilisateur, même si l'application est impliquée dans d'autres processus.  L'utilisation de plusieurs threads d'exécution est l'une des manières les plus efficaces de conserver la réactivité de votre application par rapport à l'utilisateur et d'utiliser en même temps le processeur entre ou même durant les événements utilisateur.  Cette section est une introduction aux concepts fondamentaux des threads. Elle se concentre sur les concepts des threads managés et l'utilisation des threads managés.  
  
> [!NOTE]
>  Depuis le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la programmation multithread est considérablement simplifiée grâce aux classes <xref:System.Threading.Tasks.Task?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel?displayProperty=fullName>, à [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), aux nouvelles classes de collection simultanées dans l'espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName> et à un nouveau modèle de programmation basé sur le concept de tâches plutôt que de threads.  Pour plus d'informations, consultez [Parallel Programming](../../../docs/standard/parallel-programming/index.md).  
  
## Dans cette section  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)  
 Fournit une vue d'ensemble des threads managés et explique quand utiliser plusieurs threads.  
  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 Explique comment créer, démarrer, suspendre, reprendre et abandonner des threads.  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Explique les niveaux de synchronisation, comment éviter des conditions de concurrence critique et d'interblocages, les ordinateurs à un seul processeur et à plusieurs processeurs, et d'autres questions relatives aux threads.  
  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)  
 Décrit les classes managées que vous pouvez utiliser pour synchroniser les activités des threads et les données d'objets faisant l'objet d'un accès sur différents threads, et fournit une vue d'ensemble des threads du pool.  
  
## Référence  
 <xref:System.Threading>  
 Contient des classes pour l'utilisation et la synchronisation des threads managés.  
  
 <xref:System.Collections.Concurrent>  
 Contient des classes de collection qui peuvent être utilisées en toute sécurité avec plusieurs threads.  
  
 <xref:System.Threading.Tasks>  
 Contient des classes permettant de créer et de planifier des tâches de traitement simultanées.  
  
## Rubriques connexes  
 [Domaines d'application](../../../docs/framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble des domaines d'application et leur utilisation par l'infrastructure du langage commun \(CLI\).  
  
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)  
 Décrit les opérations élémentaires des E\/S asynchrones et leurs avantages en termes de performances.  
  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Fournit une vue d'ensemble de la programmation asynchrone  
  
 [Calling Synchronous Methods Asynchronously](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Explique comment appeler des méthodes sur des threads du pool de threads à l'aide des fonctionnalités intégrées des délégués.  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 Décrit les bibliothèques de programmation parallèles, lesquelles simplifient l'utilisation de plusieurs threads dans des applications.  
  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Décrit un système permettant d'exécuter des requêtes en parallèle, afin de tirer parti de plusieurs processeurs.