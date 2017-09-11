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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eea7c94dffe525bb36c677bf3414f25ed0210074
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="43c44-102">(Visual Basic) de regroupement des threads</span><span class="sxs-lookup"><span data-stu-id="43c44-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="43c44-103">A *pool de threads* est une collection de threads qui peut être utilisé pour effectuer plusieurs tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="43c44-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="43c44-104">(Voir [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) pour plus d’informations.) Cela laisse le thread principal libre d’effectuer les tâches de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="43c44-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="43c44-105">Pools de threads sont souvent utilisés dans les applications serveur.</span><span class="sxs-lookup"><span data-stu-id="43c44-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="43c44-106">Chaque requête entrante est assignée à un thread du pool de threads, afin que la demande puisse être traitée de façon asynchrone, sans lier le thread principal ou différer le traitement des demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="43c44-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="43c44-107">Une fois qu’un thread du pool a terminé sa tâche, il est retourné à une file d’attente de threads en attente, où il peut être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="43c44-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="43c44-108">Cette réutilisation permet aux applications d’éviter le coût de création d’un nouveau thread pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="43c44-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="43c44-109">Pools de threads ont généralement un nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="43c44-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="43c44-110">Si tous les threads sont occupés, des tâches supplémentaires sont placées dans la file d’attente jusqu'à ce qu’ils puissent être gérés comme les threads deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="43c44-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="43c44-111">Vous pouvez implémenter votre propre pool de threads, mais il est plus facile d’utiliser le pool de threads fourni par le .NET Framework via la <xref:System.Threading.ThreadPool>classe.</xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="43c44-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="43c44-112">Regroupement de threads, vous appelez le <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>méthode avec un délégué pour la procédure que vous souhaitez exécuter, et Visual Basic crée le thread et exécute votre procédure.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="43c44-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="43c44-113">Exemple de regroupement des threads</span><span class="sxs-lookup"><span data-stu-id="43c44-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="43c44-114">L’exemple suivant montre comment vous pouvez utiliser le regroupement pour lancer plusieurs tâches de threads.</span><span class="sxs-lookup"><span data-stu-id="43c44-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="43c44-115">L’un des avantages du regroupement de threads sont que vous pouvez passer des arguments dans un objet d’état à la procédure de la tâche.</span><span class="sxs-lookup"><span data-stu-id="43c44-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="43c44-116">Si la procédure que vous appelez exige plusieurs arguments, vous pouvez convertir une structure ou une instance d’une classe dans un `Object` type de données.</span><span class="sxs-lookup"><span data-stu-id="43c44-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="43c44-117">Paramètres de Pool de threads et les valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="43c44-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="43c44-118">Retour de valeurs à partir d’un thread de pool de threads n’est pas simple.</span><span class="sxs-lookup"><span data-stu-id="43c44-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="43c44-119">Le moyen standard de retourner des valeurs à partir d’un appel de fonction n’est pas autorisée car `Sub` procédures sont le seul type de procédure qui peut être mises en attente pour un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="43c44-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="43c44-120">Une façon vous pouvez fournir des paramètres et retourner des valeurs consiste à encapsuler les paramètres, les valeurs de retournés et les méthodes dans un classe wrapper comme décrit dans [paramètres et valeurs de retour pour les procédures multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="43c44-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="43c44-121">Une méthode plus simple consiste à fournir des paramètres et valeurs de retour consiste à utiliser le paramètre facultatif `ByVal` variable objet d’état de la <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>méthode.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="43c44-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="43c44-122">Si vous utilisez cette variable pour transmettre une référence à une instance d’une classe, les membres de l’instance peuvent être modifiés par le thread de pool de threads et utilisés comme valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="43c44-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="43c44-123">Dans un premier temps il peut-être pas évident que vous pouvez modifier un objet référencé par une variable qui est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="43c44-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="43c44-124">Pour cela, car la référence d’objet est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="43c44-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="43c44-125">Lorsque vous apportez des modifications aux membres de l’objet référencé par la référence d’objet, les modifications s’appliquent à l’instance de la classe réelle.</span><span class="sxs-lookup"><span data-stu-id="43c44-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="43c44-126">Structures ne peuvent pas être utilisées pour retourner des valeurs dans les objets état.</span><span class="sxs-lookup"><span data-stu-id="43c44-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="43c44-127">Étant donné que les structures sont des types valeur, les modifications apportées par le processus asynchrone ne modifiez pas les membres de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="43c44-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="43c44-128">Utiliser des structures pour fournir des paramètres lorsque les valeurs de retour ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="43c44-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c44-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c44-129">See Also</span></span>  
 <span data-ttu-id="43c44-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="43c44-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="43c44-131"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="43c44-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="43c44-132"><xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="43c44-132"><xref:System.Threading.ThreadPool></span></span>   
<span data-ttu-id="43c44-133"> [Comment : utiliser un Pool de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="43c44-133"> [How to: Use a Thread Pool (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
<span data-ttu-id="43c44-134"> [Threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="43c44-134"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="43c44-135"> [Applications multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="43c44-135"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="43c44-136"> [Synchronisation de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="43c44-136"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span></span>
