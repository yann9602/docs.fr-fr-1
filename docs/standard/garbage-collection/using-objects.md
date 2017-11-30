---
title: "Utilisation d’objets implémentant IDisposable"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="c30d3-102">Utilisation d’objets implémentant IDisposable</span><span class="sxs-lookup"><span data-stu-id="c30d3-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="c30d3-103">Garbage collector du common language runtime récupère la mémoire utilisée par les objets managés, mais les types qui utilisent les ressources non managées implémentent le <xref:System.IDisposable> interface pour permettre à la mémoire allouée à des ressources non managées à être récupéré.</span><span class="sxs-lookup"><span data-stu-id="c30d3-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="c30d3-104">Une fois que vous avez fini d'utiliser un objet qui implémente <xref:System.IDisposable>, vous devez appeler l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de l'objet.</span><span class="sxs-lookup"><span data-stu-id="c30d3-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="c30d3-105">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="c30d3-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="c30d3-106">Avec l’instruction `using`C# ou l’instruction `Using`Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c30d3-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="c30d3-107">En implémentant un bloc `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="c30d3-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="c30d3-108">Instruction using</span><span class="sxs-lookup"><span data-stu-id="c30d3-108">The using statement</span></span>

<span data-ttu-id="c30d3-109">L’instruction `using`en C# et l’instruction `Using` en Visual Basic simplifient le code que vous devez écrire pour créer et nettoyer un objet.</span><span class="sxs-lookup"><span data-stu-id="c30d3-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="c30d3-110">L’instruction `using` obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l’objet.</span><span class="sxs-lookup"><span data-stu-id="c30d3-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="c30d3-111">Toutefois, l’instruction `using` est utile uniquement pour les objets utilisés dans la portée de la méthode dans laquelle elles sont construites.</span><span class="sxs-lookup"><span data-stu-id="c30d3-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="c30d3-112">L'exemple suivant utilise l'instruction `using` pour créer et libérer un objet <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c30d3-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="c30d3-113">Notez que, bien que la classe <xref:System.IO.StreamReader> implémente l'interface <xref:System.IDisposable>, ce qui signifie qu'elle utilise une ressource non managée, l'exemple n'appelle pas explicitement la méthode <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c30d3-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c30d3-114">Quand le compilateur C# ou Visual Basic rencontre l’instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="c30d3-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="c30d3-115">C# `using` instruction vous permet également d’acquérir plusieurs ressources dans une seule instruction, ce qui revient en interne imbriquée `using` instructions.</span><span class="sxs-lookup"><span data-stu-id="c30d3-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="c30d3-116">L'exemple suivant instancie deux objets <xref:System.IO.StreamReader> pour lire le contenu de deux fichiers différents.</span><span class="sxs-lookup"><span data-stu-id="c30d3-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="c30d3-117">Bloc try/finally</span><span class="sxs-lookup"><span data-stu-id="c30d3-117">Try/finally block</span></span>

<span data-ttu-id="c30d3-118">Au lieu d’encapsuler un bloc `try/finally` dans une instruction `using`, vous pouvez choisir d’implémenter le bloc `try/finally` directement.</span><span class="sxs-lookup"><span data-stu-id="c30d3-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="c30d3-119">Il peut s'agir de votre style personnel en matière de codage, ou vous pouvez procéder ainsi pour l'une des raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c30d3-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="c30d3-120">Pour insérer un bloc `catch` afin de gérer toutes les exceptions levées dans le bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="c30d3-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="c30d3-121">Sinon, toutes les exceptions levées par l’instruction `using` ne sont pas gérées, de même que toutes les exceptions levées dans le bloc `using` si un bloc `try/catch` n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="c30d3-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="c30d3-122">Pour instancier un objet qui implémente <xref:System.IDisposable> dont la portée n'est pas locale au bloc dans lequel elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="c30d3-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="c30d3-123">L’exemple suivant est similaire à l’exemple précédent, sauf qu’elle utilise un `try/catch/finally` bloc pour instancier, utiliser et supprimer un <xref:System.IO.StreamReader> objet et de gérer les exceptions levées par le <xref:System.IO.StreamReader> constructeur et ses <xref:System.IO.StreamReader.ReadToEnd%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c30d3-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="c30d3-124">Notez que le code du bloc `finally` vérifie que l'objet qui implémente <xref:System.IDisposable> n'est pas `null` avant d'appeler la méthode <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="c30d3-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="c30d3-125">La non-exécution de cette opération peut générer une <xref:System.NullReferenceException> au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c30d3-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="c30d3-126">Vous pouvez suivre ce modèle de base si vous choisissez d’implémenter ou devez implémenter un `try/finally` bloquer, car votre langage de programmation ne prend pas en charge un `using` instruction mais autorise les appels directs à la <xref:System.IDisposable.Dispose%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c30d3-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c30d3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c30d3-127">See also</span></span>

<span data-ttu-id="c30d3-128">[Nettoyage des ressources non managées](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="c30d3-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="c30d3-129">[à l’aide de l’instruction (référence c#)](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c30d3-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="c30d3-130">À l’aide de l’instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c30d3-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
