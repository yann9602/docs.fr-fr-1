---
title: "using, instruction (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-statement-c-reference"></a><span data-ttu-id="9eb88-102">using, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9eb88-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="9eb88-103">Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9eb88-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb88-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9eb88-104">Example</span></span>  
 <span data-ttu-id="9eb88-105">L’exemple suivant montre comment utiliser l’instruction using.</span><span class="sxs-lookup"><span data-stu-id="9eb88-105">The following example shows how to use the using statement.</span></span>  
  
 <span data-ttu-id="9eb88-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9eb88-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eb88-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9eb88-107">Remarks</span></span>  
 <span data-ttu-id="9eb88-108"><xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil).</span><span class="sxs-lookup"><span data-stu-id="9eb88-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="9eb88-109">Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler.</span><span class="sxs-lookup"><span data-stu-id="9eb88-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="9eb88-110">Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9eb88-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
 <span data-ttu-id="9eb88-111">En générale, quand vous utilisez un objet `IDisposable`, vous devez le déclarer et l’instancier dans une instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="9eb88-111">As a rule, when you use an `IDisposable` object, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="9eb88-112">L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée.</span><span class="sxs-lookup"><span data-stu-id="9eb88-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="9eb88-113">Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.</span><span class="sxs-lookup"><span data-stu-id="9eb88-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="9eb88-114">L’instruction `using` garantit que la méthode <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit lors de l’appel de méthodes sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="9eb88-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="9eb88-115">Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc try, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc finally ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="9eb88-115">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="9eb88-116">L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :</span><span class="sxs-lookup"><span data-stu-id="9eb88-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 <span data-ttu-id="9eb88-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9eb88-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span></span>  
  
 <span data-ttu-id="9eb88-118">Il est possible de déclarer plusieurs instances d’un type dans une instruction `using`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9eb88-118">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 <span data-ttu-id="9eb88-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9eb88-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span></span>  
  
 <span data-ttu-id="9eb88-120">Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="9eb88-120">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="9eb88-121">En effet, l’objet reste dans la portée une fois que le contrôle a quitté le bloc `using`, même s’il ne peut probablement plus accéder à ses ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="9eb88-121">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="9eb88-122">En d’autres termes, il ne sera plus complètement initialisé.</span><span class="sxs-lookup"><span data-stu-id="9eb88-122">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="9eb88-123">Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="9eb88-123">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="9eb88-124">C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="9eb88-124">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 <span data-ttu-id="9eb88-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9eb88-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9eb88-126">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9eb88-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9eb88-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eb88-127">See Also</span></span>  
 <span data-ttu-id="9eb88-128">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9eb88-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9eb88-129">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9eb88-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9eb88-130">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9eb88-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9eb88-131">[using, directive](../../../csharp/language-reference/keywords/using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="9eb88-131">[using Directive](../../../csharp/language-reference/keywords/using-directive.md) </span></span>  
 <span data-ttu-id="9eb88-132">[Garbage collection](../../../standard/garbage-collection/index.md) </span><span class="sxs-lookup"><span data-stu-id="9eb88-132">[Garbage Collection](../../../standard/garbage-collection/index.md) </span></span>  
 [<span data-ttu-id="9eb88-133">Implémentation d’une méthode Dispose</span><span class="sxs-lookup"><span data-stu-id="9eb88-133">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)

