---
title: Threads (c#) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e3f213b43c2f05a5afef1db7aec8b9c2695df989
ms.contentlocale: fr-fr
ms.lasthandoff: 06/15/2017

---
# <a name="threading-c"></a>Threads (C#)
Threading permet à votre programme c# effectuer un traitement simultané afin que vous pouvez effectuer plusieurs opérations à la fois. Par exemple, vous pouvez utiliser le threading pour surveiller l’entrée de l’utilisateur, effectuer des tâches en arrière-plan et gérer des flux simultanés d’entrée.  
  
 Threads ont les propriétés suivantes :  
  
-   Les threads permettent à votre programme effectuer un traitement simultané.  
  
-   Le .NET Framework <xref:System.Threading> rend d’espace de noms l’utilisation de threads.  
  
-   Les threads partagent les ressources de l’application. Pour plus d’informations, consultez [à l’aide de Threads et du Threading](https://msdn.microsoft.com/library/e1dx6b2h).  
  
 Par défaut, un programme c# a un thread. Toutefois, les threads auxiliaires peuvent être créés et utilisés pour exécuter du code en parallèle avec le thread principal. Ces threads sont souvent appelés *de threads de travail*.  
  
 Threads de travail peuvent être utilisés pour effectuer des tâches longues ou à durée critique sans bloquer le thread principal. Par exemple, les threads de travail sont souvent utilisés dans les applications serveur pour répondre à des requêtes entrantes sans attendre que la demande précédente doit être terminé. Threads de travail sont également utilisés pour effectuer des tâches de « en arrière-plan » dans les applications de bureau afin que le thread principal--quels lecteurs sont des éléments d’interface utilisateur--reste sensible aux actions de l’utilisateur.  
  
 Threading résout les problèmes de débit et de réactivité, mais peuvent également introduire des problèmes de partage des ressources telles que des blocages et des conditions de concurrence. Plusieurs threads sont le mieux pour les tâches qui nécessitent des ressources différentes telles que les handles de fichiers et des connexions réseau. Assigner plusieurs threads à une seule ressource est susceptible de causer des problèmes de synchronisation et avoir threads fréquemment bloquées pendant l’attente d’autres threads d’annule l’effet de l’utilisation de plusieurs threads.  
  
 Une stratégie commune consiste à utiliser des threads de travail à effectuer du temps ou des tâches en temps critique qui ne nécessitent pas beaucoup les ressources utilisées par les autres threads. Naturellement, certaines ressources dans votre programme doivent être accessible par plusieurs threads. Dans ce cas, le <xref:System.Threading> espace de noms fournit des classes pour la synchronisation de threads. Ces classes incluent <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, et <xref:System.Threading.ManualResetEvent>.  
  
 Vous pouvez utiliser tout ou partie de ces classes pour synchroniser les activités de plusieurs threads, mais une prise en charge pour le thread est pris en charge par le langage c#. Par exemple, le [instruction Lock](../../../../csharp/language-reference/keywords/lock-statement.md) fournit les fonctionnalités de synchronisation via l’utilisation implicite de <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  À partir de la [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], programmation multithread est considérablement simplifiée avec le <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> et <xref:System.Threading.Tasks.Task?displayProperty=fullName> classes, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), classes de collection simultanée nouvelle dans le <xref:System.Collections.Concurrent?displayProperty=fullName> espace de noms et un nouveau modèle de programmation basé sur le concept de tâches plutôt que de threads. Pour plus d’informations, consultez la page [Programmation parallèle](https://msdn.microsoft.com/library/dd460693).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Décrit comment créer et utiliser des threads.|  
|[Paramètres et valeurs de retour pour les procédures multithread (c#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Décrit comment passer des paramètres et de retour avec des applications multithread.|  
|[Procédure pas à pas : Multithreading avec le composant BackgroundWorker (c#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Montre comment créer une application multithread simple.|  
|[Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Décrit comment contrôler les interactions de threads.|  
|[Composants Timer thread (c#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Décrit comment exécuter des procédures sur des threads séparés à intervalles fixes.|  
|[Thread de regroupement (c#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Décrit comment utiliser un pool de threads de travail qui sont gérés par le système.|  
|[Comment : utiliser un Pool de threads (c#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Illustre l’utilisation synchronisée de plusieurs threads dans le pool de threads.|  
|[Thread](https://msdn.microsoft.com/library/3e8s7xdd)|Décrit comment implémenter des threads dans le .NET Framework.|
