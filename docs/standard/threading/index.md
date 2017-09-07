---
title: "Threading managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f2a8792818e837f019403aa84c2c2e98db0b2b89
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="managed-threading"></a>Threading managé
Que votre développement s’applique à des ordinateurs avec un ou plusieurs processeurs, votre application doit fournir l’interaction la plus réactive avec l’utilisateur, même si l’application effectue actuellement d’autres opérations. Utiliser plusieurs threads d’exécution est l’une des manières les plus efficaces pour maintenir la réactivité de votre application vis-à-vis de l’utilisateur, tout en exploitant le processeur entre voire pendant des événements utilisateur. Bien que cette section présente les concepts de base du threading, elle se concentre sur les concepts de threading managé et son utilisation.  
  
> [!NOTE]
>  À compter du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> et <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=fullName>, et un nouveau modèle de programmation basé sur le concept de tâches plutôt que de threads. Pour plus d’informations, consultez la page [Programmation parallèle](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Éléments fondamentaux du threading managé](../../../docs/standard/threading/managed-threading-basics.md)  
 Fournit une vue d’ensemble des threads managés et explique quand utiliser plusieurs threads.  
  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 Explique comment créer, démarrer, suspendre, reprendre et abandonner des threads.  
  
 [Bonnes pratiques de threading géré](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Décrit les niveaux de synchronisation, comment éviter les interblocages et les conditions de concurrence, les ordinateurs à un ou plusieurs processeurs et les autres problèmes liés aux threads.  
  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 Décrit les classes managées que vous pouvez utiliser pour synchroniser les activités de threads et les données d’objets ouvertes sur différents threads, et fournit une vue d’ensemble des threads du pool.  
  
## <a name="reference"></a>Référence  
 <xref:System.Threading>  
 Contient des classes pour l’utilisation et la synchronisation de threads managés.  
  
 <xref:System.Collections.Concurrent>  
 Contient des classes de collection qui peuvent être utilisées en toute sécurité avec plusieurs threads.  
  
 <xref:System.Threading.Tasks>  
 Contient des classes pour la création et la planification de tâches de traitement simultanées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Domaines d’application](../../../docs/framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble des domaines d'application et de leur utilisation dans le Common Language Infrastructure.  
  
 [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Décrit les opérations élémentaires des E/S asynchrones et leurs avantages en termes de performances.  
  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Fournit une vue d'ensemble de la programmation asynchrone.  
  
 [Appel de méthodes synchrones de façon asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Explique comment appeler des méthodes sur les threads d’un pool à l’aide des fonctionnalités intégrées des délégués.  
  
 [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)  
 Décrit les bibliothèques de programmation parallèle qui simplifient l’utilisation de plusieurs threads dans les applications.  
  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Décrit un système permettant d’exécuter des requêtes en parallèle afin de tirer parti de plusieurs processeurs.

