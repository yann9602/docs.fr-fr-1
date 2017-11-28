---
title: Threads (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 633fe784b98bf67086581b82fb4b00cff28d5f5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="threading-c"></a>Threads (C#)
Les threads donnent la possibilité à votre programme C# d’effectuer des traitements simultanés, ce qui vous permet de faire plusieurs opérations à la fois. Par exemple, vous pouvez utiliser les threads pour surveiller les entrées de l’utilisateur, effectuer des tâches en arrière-plan et gérer des flux d’entrée simultanés.  
  
 Les threads ont les propriétés suivantes :  
  
-   Les threads permettent à votre programme d’effectuer un traitement simultané.  
  
-   L’espace de noms <xref:System.Threading> du .NET Framework facilite l’utilisation des threads.  
  
-   Les threads partagent les ressources de l’application. Pour plus d’informations, consultez [Using Threads and Threading](https://msdn.microsoft.com/library/e1dx6b2h).  
  
 Par défaut, un programme C# a un seul thread. Cependant, vous pouvez créer et utiliser des threads auxiliaires pour exécuter du code en parallèle avec le thread principal. Ces threads sont souvent appelés des *threads de travail*.  
  
 Les threads de travail peuvent être utilisés pour effectuer des tâches longues ou à durée critique sans bloquer le thread principal. Par exemple, les threads de travail sont souvent utilisés dans les applications serveur pour répondre à des demandes entrantes sans attendre que la demande précédente soit terminée. Les threads de travail sont également utilisés pour effectuer des tâches « en arrière-plan » dans les applications de poste de travail pour que le thread principal, qui pilote les éléments de l’interface utilisateur, continue de répondre aux actions de l’utilisateur.  
  
 Les threads résolvent les problèmes de débit et de réactivité, mais ils peuvent aussi introduire des problèmes de partage des ressources, comme des interblocages et des situations de concurrence. Les threads multiples conviennent mieux pour les tâches qui nécessitent des ressources différentes, comme les descripteurs de fichiers et les connexions réseau. L’affectation de plusieurs threads à une même ressource risque de provoquer des problèmes de synchronisation et d’aboutir au blocage fréquent des threads dans l’attente d’autres threads, ce qui est contraire à l’objectif poursuivi par l’utilisation de plusieurs threads.  
  
 Une stratégie courante consiste à utiliser des threads de travail pour effectuer des tâches longues ou à durée critique qui nécessitent peu les ressources utilisées par d’autres threads. Naturellement, plusieurs threads doivent accéder à certaines ressources de votre programme. Pour ces situations, l’espace de noms <xref:System.Threading> fournit des classes pour la synchronisation des threads. Ces classes sont <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent>.  
  
 Vous pouvez utiliser tout ou partie de ces classes pour synchroniser les activités de plusieurs threads, mais le langage C# offre lui-même une certaine prise en charge des threads. Par exemple, l’[instruction Lock](../../../../csharp/language-reference/keywords/lock-statement.md) fournit des fonctionnalités de synchronisation via l’utilisation implicite de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  À compter du [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>, et un nouveau modèle de programmation basé sur le concept de tâche au lieu de celui de thread. Pour plus d’informations, consultez la page [Programmation parallèle](https://msdn.microsoft.com/library/dd460693).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Explique comment créer et utiliser les threads.|  
|[Paramètres et valeurs de retour pour les procédures multithreads (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Décrit comment passer et retourner des paramètres avec des applications multithreads.|  
|[Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Montre comment créer une application multithread simple.|  
|[Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Décrit comment contrôler les interactions des threads.|  
|[Minuteurs de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Décrit comment exécuter des procédures sur des threads distincts à intervalles fixes.|  
|[Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Décrit comment utiliser un pool de threads de travail qui sont gérés par le système.|  
|[Guide pratique pour utiliser un pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Montre l’utilisation synchronisée de plusieurs threads dans le pool de threads.|  
|[Thread](https://msdn.microsoft.com/library/3e8s7xdd)|Décrit comment implémenter des threads dans le .NET Framework.|
