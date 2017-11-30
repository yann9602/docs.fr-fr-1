---
title: "Création de threads et passage de données au démarrage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="a92c5-102">Création de threads et passage de données au démarrage</span><span class="sxs-lookup"><span data-stu-id="a92c5-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="a92c5-103">Lorsqu’un processus de système d’exploitation est créé, le système d’exploitation injecte un thread pour exécuter du code dans ce processus, y compris un domaine d’application d’origine.</span><span class="sxs-lookup"><span data-stu-id="a92c5-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="a92c5-104">À ce stade, les domaines d’application peuvent être créés et détruits sans aucun thread de système d’exploitation nécessairement créée ou détruite.</span><span class="sxs-lookup"><span data-stu-id="a92c5-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="a92c5-105">Si le code en cours d’exécution est géré code, puis un <xref:System.Threading.Thread> de l’objet pour le thread s’exécutant dans le domaine d’application actuel peut être obtenu en récupérant statiques <xref:System.Threading.Thread.CurrentThread%2A> propriété de type <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="a92c5-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="a92c5-106">Cette rubrique décrit la création de threads et présente des alternatives pour passer des données à la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="a92c5-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="a92c5-107">Création d’un Thread</span><span class="sxs-lookup"><span data-stu-id="a92c5-107">Creating a Thread</span></span>  
 <span data-ttu-id="a92c5-108">Création d’un nouveau <xref:System.Threading.Thread> objet crée un thread managé.</span><span class="sxs-lookup"><span data-stu-id="a92c5-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="a92c5-109">Le <xref:System.Threading.Thread> classe a des constructeurs qui acceptent un <xref:System.Threading.ThreadStart> délégué ou un <xref:System.Threading.ParameterizedThreadStart> déléguer ; le délégué encapsule la méthode qui est appelée par le nouveau thread lorsque vous appelez le <xref:System.Threading.Thread.Start%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="a92c5-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="a92c5-110">Appel de <xref:System.Threading.Thread.Start%2A> plusieurs fois entraîne un <xref:System.Threading.ThreadStateException> levée.</span><span class="sxs-lookup"><span data-stu-id="a92c5-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="a92c5-111">Le <xref:System.Threading.Thread.Start%2A> méthode retourne immédiatement, souvent avant que le nouveau thread a réellement démarré.</span><span class="sxs-lookup"><span data-stu-id="a92c5-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="a92c5-112">Vous pouvez utiliser la <xref:System.Threading.Thread.ThreadState%2A> et <xref:System.Threading.Thread.IsAlive%2A> propriétés afin de déterminer l’état du thread à tout moment, mais ces propriétés ne doivent jamais être utilisé pour synchroniser les activités de threads.</span><span class="sxs-lookup"><span data-stu-id="a92c5-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a92c5-113">Une fois qu’un thread est démarré, il n’est pas nécessaire de conserver une référence à la <xref:System.Threading.Thread> objet.</span><span class="sxs-lookup"><span data-stu-id="a92c5-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="a92c5-114">Le thread continue à s’exécuter jusqu'à la fin de la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="a92c5-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="a92c5-115">L’exemple de code suivant crée deux nouveaux threads pour appeler des méthodes statiques et instance sur un autre objet.</span><span class="sxs-lookup"><span data-stu-id="a92c5-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="a92c5-116">Passer des données à des Threads et la récupération des données à partir de Threads</span><span class="sxs-lookup"><span data-stu-id="a92c5-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="a92c5-117">Dans le .NET Framework version 2.0, le <xref:System.Threading.ParameterizedThreadStart> délégué offre un moyen facile de passer un objet contenant les données à un thread lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> surcharge de méthode.</span><span class="sxs-lookup"><span data-stu-id="a92c5-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="a92c5-118">Pour obtenir un exemple de code, consultez <xref:System.Threading.ParameterizedThreadStart>.</span><span class="sxs-lookup"><span data-stu-id="a92c5-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="a92c5-119">À l’aide de la <xref:System.Threading.ParameterizedThreadStart> délégué n’est pas de type sécurisé permet de passer des données, car le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> surcharge de méthode accepte tout objet.</span><span class="sxs-lookup"><span data-stu-id="a92c5-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="a92c5-120">Une alternative consiste à encapsuler la procédure de thread et les données dans une classe d’assistance et à utiliser le <xref:System.Threading.ThreadStart> délégué à exécuter la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="a92c5-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="a92c5-121">Cette technique est illustrée dans les deux exemples de code qui suivent.</span><span class="sxs-lookup"><span data-stu-id="a92c5-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="a92c5-122">Aucune de ces délégués a une valeur de retour, car il n’existe pas de place pour retourner les données à partir d’un appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a92c5-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="a92c5-123">Pour récupérer les résultats d’une méthode de thread, vous pouvez utiliser une méthode de rappel, comme illustré dans le deuxième exemple de code.</span><span class="sxs-lookup"><span data-stu-id="a92c5-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="a92c5-124">La récupération des données avec les méthodes de rappel</span><span class="sxs-lookup"><span data-stu-id="a92c5-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="a92c5-125">L’exemple suivant montre une méthode de rappel qui Récupère des données à partir d’un thread.</span><span class="sxs-lookup"><span data-stu-id="a92c5-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="a92c5-126">Le constructeur de la classe qui contient les données et la méthode de thread accepte également un délégué qui représente la méthode de rappel ; avant la fin de la méthode de thread, il appelle le délégué de rappel.</span><span class="sxs-lookup"><span data-stu-id="a92c5-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a92c5-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a92c5-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a92c5-128">Thread</span><span class="sxs-lookup"><span data-stu-id="a92c5-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="a92c5-129">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="a92c5-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
