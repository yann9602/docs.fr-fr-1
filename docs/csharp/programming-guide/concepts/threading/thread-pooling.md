---
title: Regroupement des threads (C#)
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
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2f8e5a2d7a83dc6fef72ef87b4003ae49656d8f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="thread-pooling-c"></a><span data-ttu-id="1715e-102">Regroupement des threads (C#)</span><span class="sxs-lookup"><span data-stu-id="1715e-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="1715e-103">Un *pool de threads* est une collection de threads qui peut être utilisée pour effectuer plusieurs tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="1715e-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="1715e-104">(Voir [Threads (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) pour obtenir des informations générales.) Cela laisse le thread principal libre d’effectuer d’autres tâches de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="1715e-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="1715e-105">Les pools de threads sont souvent utilisés dans des applications serveur.</span><span class="sxs-lookup"><span data-stu-id="1715e-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="1715e-106">Chaque demande entrante est assignée à un thread du pool de threads pour pouvoir être traitée de façon asynchrone, sans lier le thread principal ni différer le traitement des demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1715e-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="1715e-107">Une fois qu’un thread du pool a terminé sa tâche, il est retourné à une file d’attente de threads en attente, où il peut être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="1715e-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="1715e-108">Cette réutilisation permet aux applications d’éviter le coût lié à la création d’un nouveau thread pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="1715e-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="1715e-109">Les pools de threads ont généralement un nombre maximal de threads.</span><span class="sxs-lookup"><span data-stu-id="1715e-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="1715e-110">Si tous les threads sont occupés, les tâches supplémentaires sont mises en file d’attente jusqu’à ce qu’elles puissent être traitées quand des threads deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="1715e-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="1715e-111">Vous pouvez implémenter votre propre pool de threads, mais il est plus facile d’utiliser le pool de threads fourni par le .NET Framework via la classe <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="1715e-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="1715e-112">Avec le regroupement de threads, vous appelez la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> avec un délégué pour la procédure que vous voulez exécuter, et C# crée le thread et exécute votre procédure.</span><span class="sxs-lookup"><span data-stu-id="1715e-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="1715e-113">Exemple d’utilisation du regroupement des threads</span><span class="sxs-lookup"><span data-stu-id="1715e-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="1715e-114">L’exemple suivant montre comment utiliser le regroupement des threads pour démarrer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="1715e-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="1715e-115">L’un des avantages du regroupement des threads est de permettre de passer des arguments dans un objet d’état à la procédure de tâche.</span><span class="sxs-lookup"><span data-stu-id="1715e-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="1715e-116">Si la procédure que vous appelez exige plusieurs arguments, vous pouvez caster une structure ou une instance d’une classe en type de données `Object`.</span><span class="sxs-lookup"><span data-stu-id="1715e-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="1715e-117">Paramètres de pool de threads et valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="1715e-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="1715e-118">Retourner des valeurs à partir d’un thread de pool de threads n’est pas une opération simple.</span><span class="sxs-lookup"><span data-stu-id="1715e-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="1715e-119">La manière standard de retourner des valeurs à partir d’un appel de fonction n’est pas autorisée, car les procédures `Sub` sont le seul type de procédure qui peut être mis en file d’attente pour être traité par un pool de threads.</span><span class="sxs-lookup"><span data-stu-id="1715e-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="1715e-120">Une façon de fournir des paramètres et de retourner des valeurs consiste à encapsuler les paramètres, les valeurs de retour et les méthodes dans une classe wrapper, comme cela est décrit dans [Paramètres et valeurs de retour pour les procédures multithread (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1715e-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="1715e-121">Une méthode plus simple de fournir des paramètres et de retourner des valeurs consiste à utiliser la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="1715e-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="1715e-122">Si vous utilisez cette variable pour transmettre une référence à une instance d’une classe, les membres de cette instance peuvent être modifiés par le thread de pool de threads et utilisés comme valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="1715e-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="1715e-123">Au début, il n’est peut-être pas évident que vous pouvez modifier un objet référencé par une variable qui est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="1715e-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="1715e-124">Vous pouvez le faire, car seule la référence de l’objet est passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="1715e-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="1715e-125">Quand vous apportez des modifications aux membres de l’objet référencé par la référence d’objet, les modifications s’appliquent à l’instance de la classe réelle.</span><span class="sxs-lookup"><span data-stu-id="1715e-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="1715e-126">Les structures ne permettent pas de retourner des valeurs au sein des objets d’état.</span><span class="sxs-lookup"><span data-stu-id="1715e-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="1715e-127">Comme les structures sont des types valeur, les modifications apportées par le processus asynchrone ne modifient pas les membres de la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="1715e-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="1715e-128">Utilisez des structures pour fournir des paramètres lorsque les valeurs de retour ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="1715e-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1715e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1715e-129">See Also</span></span>  
 <span data-ttu-id="1715e-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="1715e-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="1715e-131"><xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="1715e-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="1715e-132"><xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="1715e-132"><xref:System.Threading.ThreadPool></span></span>   
 <span data-ttu-id="1715e-133">[Guide pratique pour utiliser un pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="1715e-133">[How to: Use a Thread Pool (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
 <span data-ttu-id="1715e-134">[Threads (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="1715e-134">[Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span></span>  
 <span data-ttu-id="1715e-135">[Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="1715e-135">[Multithreaded Applications (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
 [<span data-ttu-id="1715e-136">Synchronisation des threads (C#)</span><span class="sxs-lookup"><span data-stu-id="1715e-136">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)

