---
title: (Visual Basic) de regroupement des threads | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6037d7ea17e260d44bae571aa25d413996f5a123
ms.lasthandoff: 03/13/2017

---
# <a name="thread-pooling-visual-basic"></a>(Visual Basic) de regroupement des threads
A *pool de threads* est une collection de threads qui peut être utilisé pour effectuer plusieurs tâches en arrière-plan. (Voir [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) pour plus d’informations.) Cela laisse le thread principal libre d’effectuer les tâches de façon asynchrone.  
  
 Pools de threads sont souvent utilisés dans les applications serveur. Chaque requête entrante est assignée à un thread du pool de threads, afin que la demande puisse être traitée de façon asynchrone, sans lier le thread principal ou différer le traitement des demandes suivantes.  
  
 Une fois qu’un thread du pool a terminé sa tâche, il est retourné à une file d’attente de threads en attente, où il peut être réutilisé. Cette réutilisation permet aux applications d’éviter le coût de création d’un nouveau thread pour chaque tâche.  
  
 Pools de threads ont généralement un nombre maximal de threads. Si tous les threads sont occupés, des tâches supplémentaires sont placées dans la file d’attente jusqu'à ce qu’ils puissent être gérés comme les threads deviennent disponibles.  
  
 Vous pouvez implémenter votre propre pool de threads, mais il est plus facile d’utiliser le pool de threads fourni par le .NET Framework via la <xref:System.Threading.ThreadPool>classe.</xref:System.Threading.ThreadPool>  
  
 Regroupement de threads, vous appelez le <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>méthode avec un délégué pour la procédure que vous souhaitez exécuter, et Visual Basic crée le thread et exécute votre procédure.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>  
  
## <a name="thread-pooling-example"></a>Exemple de regroupement des threads  
 L’exemple suivant montre comment vous pouvez utiliser le regroupement pour lancer plusieurs tâches de threads.  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 L’un des avantages du regroupement de threads sont que vous pouvez passer des arguments dans un objet d’état à la procédure de la tâche. Si la procédure que vous appelez exige plusieurs arguments, vous pouvez convertir une structure ou une instance d’une classe dans un `Object` type de données.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Paramètres de Pool de threads et les valeurs de retour  
 Retour de valeurs à partir d’un thread de pool de threads n’est pas simple. Le moyen standard de retourner des valeurs à partir d’un appel de fonction n’est pas autorisée car `Sub` procédures sont le seul type de procédure qui peut être mises en attente pour un pool de threads. Une façon vous pouvez fournir des paramètres et retourner des valeurs consiste à encapsuler les paramètres, les valeurs de retournés et les méthodes dans un classe wrapper comme décrit dans [paramètres et valeurs de retour pour les procédures multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 Une méthode plus simple consiste à fournir des paramètres et valeurs de retour consiste à utiliser le paramètre facultatif `ByVal` variable objet d’état de la <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>méthode.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> Si vous utilisez cette variable pour transmettre une référence à une instance d’une classe, les membres de l’instance peuvent être modifiés par le thread de pool de threads et utilisés comme valeurs de retour.  
  
 Dans un premier temps il peut-être pas évident que vous pouvez modifier un objet référencé par une variable qui est passée par valeur. Pour cela, car la référence d’objet est passée par valeur. Lorsque vous apportez des modifications aux membres de l’objet référencé par la référence d’objet, les modifications s’appliquent à l’instance de la classe réelle.  
  
 Structures ne peuvent pas être utilisées pour retourner des valeurs dans les objets état. Étant donné que les structures sont des types valeur, les modifications apportées par le processus asynchrone ne modifiez pas les membres de la structure d’origine. Utiliser des structures pour fournir des paramètres lorsque les valeurs de retour ne sont pas nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool>   
 [Comment : utiliser un Pool de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)   
 [Threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Synchronisation de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
