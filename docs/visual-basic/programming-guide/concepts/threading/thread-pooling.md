---
title: (Visual Basic) de regroupement des threads
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="b4878-102">(Visual Basic) de regroupement des threads</span><span class="sxs-lookup"><span data-stu-id="b4878-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="b4878-103">Un *pool de threads* est une collection de threads qui peut être utilisée pour effectuer plusieurs tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b4878-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="b4878-104">(Consultez [threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) pour plus d’informations.) Cela laisse le thread principal libre d’effectuer d’autres tâches de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b4878-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="b4878-105">Les pools de threads sont souvent utilisés dans des applications serveur.</span><span class="sxs-lookup"><span data-stu-id="b4878-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="b4878-106">Chaque demande entrante est assignée à un thread du pool de threads pour pouvoir être traitée de façon asynchrone, sans lier le thread principal ni différer le traitement des demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b4878-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="b4878-107">Une fois qu’un thread du pool a terminé sa tâche, il est retourné à une file d’attente de threads en attente, où il peut être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="b4878-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="b4878-108">Cette réutilisation permet aux applications d’éviter le coût lié à la création d’un nouveau thread pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="b4878-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="b4878-109">Les pools de threads ont généralement un nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="b4878-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="b4878-110">Si tous les threads sont occupés, les tâches supplémentaires sont mises en file d’attente jusqu’à ce qu’elles puissent être traitées quand des threads deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="b4878-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="b4878-111">Vous pouvez implémenter votre propre pool de threads, mais il est plus facile d’utiliser le pool de threads fourni par le .NET Framework via la classe <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="b4878-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="b4878-112">Regroupement de threads, vous appelez le <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> méthode avec un délégué pour la procédure que vous souhaitez exécuter, et Visual Basic crée le thread et exécute votre procédure.</span><span class="sxs-lookup"><span data-stu-id="b4878-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="b4878-113">Exemple d’utilisation du regroupement des threads</span><span class="sxs-lookup"><span data-stu-id="b4878-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="b4878-114">L’exemple suivant montre comment utiliser le regroupement des threads pour démarrer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="b4878-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="b4878-115">L’un des avantages du regroupement des threads est de permettre de passer des arguments dans un objet d’état à la procédure de tâche.</span><span class="sxs-lookup"><span data-stu-id="b4878-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="b4878-116">Si la procédure que vous appelez exige plusieurs arguments, vous pouvez caster une structure ou une instance d’une classe en type de données `Object`.</span><span class="sxs-lookup"><span data-stu-id="b4878-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="b4878-117">Paramètres de pool de threads et valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="b4878-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="b4878-118">Retourner des valeurs à partir d’un thread de pool de threads n’est pas une opération simple.</span><span class="sxs-lookup"><span data-stu-id="b4878-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="b4878-119">La manière standard de retourner des valeurs à partir d’un appel de fonction n’est pas autorisée, car les procédures `Sub` sont le seul type de procédure qui peut être mis en file d’attente pour être traité par un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="b4878-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="b4878-120">Une façon vous pouvez fournir des paramètres et retourner des valeurs consiste à encapsuler les paramètres, les valeurs de retour, et les méthodes dans un wrapper de classe comme décrit dans [paramètres et valeurs de retour pour les procédures multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b4878-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="b4878-121">Une méthode plus simple de fournir des paramètres et de retourner des valeurs consiste à utiliser la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4878-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="b4878-122">Si vous utilisez cette variable pour transmettre une référence à une instance d’une classe, les membres de cette instance peuvent être modifiés par le thread de pool de threads et utilisés comme valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="b4878-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="b4878-123">Au début, il n’est peut-être pas évident que vous pouvez modifier un objet référencé par une variable qui est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="b4878-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="b4878-124">Vous pouvez le faire, car seule la référence de l’objet est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="b4878-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="b4878-125">Quand vous apportez des modifications aux membres de l’objet référencé par la référence d’objet, les modifications s’appliquent à l’instance de la classe réelle.</span><span class="sxs-lookup"><span data-stu-id="b4878-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="b4878-126">Les structures ne permettent pas de retourner des valeurs au sein des objets d’état.</span><span class="sxs-lookup"><span data-stu-id="b4878-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="b4878-127">Comme les structures sont des types valeur, les modifications apportées par le processus asynchrone ne modifient pas les membres de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="b4878-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="b4878-128">Utilisez des structures pour fournir des paramètres lorsque les valeurs de retour ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b4878-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4878-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4878-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="b4878-130">Guide pratique pour utiliser un pool de threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4878-130">How to: Use a Thread Pool (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="b4878-131">Threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4878-131">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="b4878-132">Applications multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4878-132">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="b4878-133">Synchronisation des threads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4878-133">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
