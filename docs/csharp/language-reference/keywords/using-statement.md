---
title: "using, instruction (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="884bf-102">using, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="884bf-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="884bf-103">Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="884bf-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="884bf-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="884bf-104">Example</span></span>  
 <span data-ttu-id="884bf-105">L’exemple suivant montre comment utiliser l’instruction using.</span><span class="sxs-lookup"><span data-stu-id="884bf-105">The following example shows how to use the using statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="884bf-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="884bf-106">Remarks</span></span>  
 <span data-ttu-id="884bf-107"><xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil).</span><span class="sxs-lookup"><span data-stu-id="884bf-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="884bf-108">Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler.</span><span class="sxs-lookup"><span data-stu-id="884bf-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="884bf-109">Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="884bf-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="884bf-110">Lorsque la durée de vie d’un `IDisposable` objet est limité à une méthode unique, vous devez déclarer et instancier dans un `using` instruction.</span><span class="sxs-lookup"><span data-stu-id="884bf-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="884bf-111">L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée.</span><span class="sxs-lookup"><span data-stu-id="884bf-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="884bf-112">Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.</span><span class="sxs-lookup"><span data-stu-id="884bf-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="884bf-113">L’instruction `using` garantit que la méthode <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit lors de l’appel de méthodes sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="884bf-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="884bf-114">Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc try, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc finally ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="884bf-114">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="884bf-115">L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :</span><span class="sxs-lookup"><span data-stu-id="884bf-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 <span data-ttu-id="884bf-116">Il est possible de déclarer plusieurs instances d’un type dans une instruction `using`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="884bf-116">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="884bf-117">Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="884bf-117">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="884bf-118">En effet, l’objet reste dans la portée une fois que le contrôle a quitté le bloc `using`, même s’il ne peut probablement plus accéder à ses ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="884bf-118">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="884bf-119">En d’autres termes, il ne sera plus complètement initialisé.</span><span class="sxs-lookup"><span data-stu-id="884bf-119">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="884bf-120">Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="884bf-120">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="884bf-121">C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="884bf-121">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="884bf-122">Pour plus d’informations sur la suppression de `IDisposable` , consultez [à l’aide des objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="884bf-122">For more information on disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="884bf-123">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="884bf-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="884bf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="884bf-124">See Also</span></span>  
 [<span data-ttu-id="884bf-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="884bf-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="884bf-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="884bf-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="884bf-127">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="884bf-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="884bf-128">using, directive</span><span class="sxs-lookup"><span data-stu-id="884bf-128">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="884bf-129">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="884bf-129">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="884bf-130">Utilisation d’objets implémentant IDisposable</span><span class="sxs-lookup"><span data-stu-id="884bf-130">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="884bf-131">Interface IDisposable</span><span class="sxs-lookup"><span data-stu-id="884bf-131">IDisposable interface</span></span>](xref:System.IDisposable)
