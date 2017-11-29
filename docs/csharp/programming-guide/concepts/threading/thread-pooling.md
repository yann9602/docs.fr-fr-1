---
title: Regroupement des threads (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: "5"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 09dd597e8ac7a6b336f71891ccc89984ea659614
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-c"></a>Regroupement des threads (C#)
Un *pool de threads* est une collection de threads qui peut être utilisée pour effectuer plusieurs tâches en arrière-plan. (Voir [Threads (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) pour obtenir des informations générales.) Cela laisse le thread principal libre d’effectuer d’autres tâches de façon asynchrone.  
  
 Les pools de threads sont souvent utilisés dans des applications serveur. Chaque demande entrante est assignée à un thread du pool de threads pour pouvoir être traitée de façon asynchrone, sans lier le thread principal ni différer le traitement des demandes suivantes.  
  
 Une fois qu’un thread du pool a terminé sa tâche, il est retourné à une file d’attente de threads en attente, où il peut être réutilisé. Cette réutilisation permet aux applications d’éviter le coût lié à la création d’un nouveau thread pour chaque tâche.  
  
 Les pools de threads ont généralement un nombre maximal de threads. Si tous les threads sont occupés, les tâches supplémentaires sont mises en file d’attente jusqu’à ce qu’elles puissent être traitées quand des threads deviennent disponibles.  
  
 Vous pouvez implémenter votre propre pool de threads, mais il est plus facile d’utiliser le pool de threads fourni par le .NET Framework via la classe <xref:System.Threading.ThreadPool>.  
  
 Avec le regroupement de threads, vous appelez la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> avec un délégué pour la procédure que vous voulez exécuter, et C# crée le thread et exécute votre procédure.  
  
## <a name="thread-pooling-example"></a>Exemple d’utilisation du regroupement des threads  
 L’exemple suivant montre comment utiliser le regroupement des threads pour démarrer plusieurs tâches.  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 L’un des avantages du regroupement des threads est de permettre de passer des arguments dans un objet d’état à la procédure de tâche. Si la procédure que vous appelez exige plusieurs arguments, vous pouvez caster une structure ou une instance d’une classe en type de données `Object`.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Paramètres de pool de threads et valeurs de retour  
 Retourner des valeurs à partir d’un thread de pool de threads n’est pas une opération simple. La manière standard de retourner des valeurs à partir d’un appel de fonction n’est pas autorisée, car les procédures `Sub` sont le seul type de procédure qui peut être mis en file d’attente pour être traité par un pool de threads. Une façon de fournir des paramètres et de retourner des valeurs consiste à encapsuler les paramètres, les valeurs de retour et les méthodes dans une classe wrapper, comme cela est décrit dans [Paramètres et valeurs de retour pour les procédures multithread (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 Une méthode plus simple de fournir des paramètres et de retourner des valeurs consiste à utiliser la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Si vous utilisez cette variable pour transmettre une référence à une instance d’une classe, les membres de cette instance peuvent être modifiés par le thread de pool de threads et utilisés comme valeurs de retour.  
  
 Au début, il n’est peut-être pas évident que vous pouvez modifier un objet référencé par une variable qui est passée par valeur. Vous pouvez le faire, car seule la référence de l’objet est passée par valeur. Quand vous apportez des modifications aux membres de l’objet référencé par la référence d’objet, les modifications s’appliquent à l’instance de la classe réelle.  
  
 Les structures ne permettent pas de retourner des valeurs au sein des objets d’état. Comme les structures sont des types valeur, les modifications apportées par le processus asynchrone ne modifient pas les membres de la structure d’origine. Utilisez des structures pour fournir des paramètres lorsque les valeurs de retour ne sont pas nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Guide pratique pour utiliser un pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
