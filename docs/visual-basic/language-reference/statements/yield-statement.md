---
title: yield, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99f5129d5cb43cddfb17731f337a72fae22d3626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="e08e9-102">yield, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e08e9-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="e08e9-103">Envoie l’élément suivant d’un regroupement à un `For Each...Next` instruction.</span><span class="sxs-lookup"><span data-stu-id="e08e9-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e08e9-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e08e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e08e9-105">Parameters</span></span>  
  
|<span data-ttu-id="e08e9-106">Terme</span><span class="sxs-lookup"><span data-stu-id="e08e9-106">Term</span></span>|<span data-ttu-id="e08e9-107">Définition</span><span class="sxs-lookup"><span data-stu-id="e08e9-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="e08e9-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e08e9-108">Required.</span></span> <span data-ttu-id="e08e9-109">Une expression qui est implicitement convertible au type de la fonction d’itérateur ou `Get` accesseur qui contienne la `Yield` instruction.</span><span class="sxs-lookup"><span data-stu-id="e08e9-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e08e9-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e08e9-110">Remarks</span></span>  
 <span data-ttu-id="e08e9-111">La `Yield` instruction retourne un élément d’une collection à la fois.</span><span class="sxs-lookup"><span data-stu-id="e08e9-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="e08e9-112">Le `Yield` instruction est incluse dans une fonction d’itérateur ou `Get` accesseur, qui effectuent des itérations personnalisées sur une collection.</span><span class="sxs-lookup"><span data-stu-id="e08e9-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="e08e9-113">Vous consommez une fonction d’itérateur en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="e08e9-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="e08e9-114">Chaque itération de la `For Each` boucle appelle la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="e08e9-115">Lorsqu’un `Yield` instruction est atteint dans la fonction d’itérateur, `expression` est renvoyé, et l’emplacement actuel dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="e08e9-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="e08e9-116">L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.</span><span class="sxs-lookup"><span data-stu-id="e08e9-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="e08e9-117">Une conversion implicite doit exister entre le type de `expression` dans la `Yield` instruction pour le type de retour de l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="e08e9-118">Vous pouvez utiliser un `Exit Function` ou `Return` instruction à la fin de l’itération.</span><span class="sxs-lookup"><span data-stu-id="e08e9-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="e08e9-119">« Produit » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’il est utilisé dans une `Iterator` fonction ou `Get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="e08e9-120">Pour plus d’informations sur les fonctions d’itérateur et `Get` accesseurs, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e08e9-120">For more information about iterator functions and `Get` accessors, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="e08e9-121">Fonctions d’itérateur et accesseurs Get</span><span class="sxs-lookup"><span data-stu-id="e08e9-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="e08e9-122">La déclaration d’une fonction d’itérateur ou `Get` accesseur doit remplir les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e08e9-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="e08e9-123">Il doit inclure un [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md) modificateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="e08e9-124">Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="e08e9-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="e08e9-125">Il ne peut avoir aucune `ByRef` paramètres.</span><span class="sxs-lookup"><span data-stu-id="e08e9-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="e08e9-126">Une fonction d’itérateur ne peut pas se produire dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.</span><span class="sxs-lookup"><span data-stu-id="e08e9-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="e08e9-127">Une fonction d’itérateur peut être une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="e08e9-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="e08e9-128">Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e08e9-128">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="e08e9-129">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="e08e9-129">Exception Handling</span></span>  
 <span data-ttu-id="e08e9-130">A `Yield` instruction peut être à l’intérieur d’un `Try` bloc d’un [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e08e9-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="e08e9-131">A `Try` bloc qui a un `Yield` instruction peut avoir `Catch` bloque et peut avoir un `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="e08e9-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="e08e9-132">A `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou une `Finally` bloc.</span><span class="sxs-lookup"><span data-stu-id="e08e9-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="e08e9-133">Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, une `Catch` bloc dans la fonction d’itérateur n’est pas exécutée, mais un `Finally` bloc dans la fonction d’itérateur est exécuté.</span><span class="sxs-lookup"><span data-stu-id="e08e9-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="e08e9-134">A `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="e08e9-135">Implémentation technique</span><span class="sxs-lookup"><span data-stu-id="e08e9-135">Technical Implementation</span></span>  
 <span data-ttu-id="e08e9-136">Le code suivant retourne un `IEnumerable (Of String)` à partir d’une fonction d’itérateur parcourt ensuite les éléments de la `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="e08e9-137">L’appel à `MyIteratorFunction` n’exécute pas le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e08e9-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="e08e9-138">À la place, l'appel retourne `IEnumerable(Of String)` dans la variable `elements`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="e08e9-139">Dans une itération de la boucle `For Each`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="e08e9-140">Cet appel exécute le corps de `MyIteratorFunction` jusqu'à ce que l'instruction `Yield` suivante soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="e08e9-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="e08e9-141">Le `Yield` instruction retourne une expression qui détermine non seulement la valeur de la `element` variable pour la consommation par le corps de la boucle, mais également le <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriété d’éléments, qui est un `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="e08e9-142">À chaque itération suivante de la boucle `For Each`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `Yield`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="e08e9-143">Le `For Each` boucle termine lorsque la fin de la fonction d’itérateur ou une `Return` ou `Exit Function` instruction est atteinte.</span><span class="sxs-lookup"><span data-stu-id="e08e9-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e08e9-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="e08e9-144">Example</span></span>  
 <span data-ttu-id="e08e9-145">L’exemple suivant comprend une `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle.</span><span class="sxs-lookup"><span data-stu-id="e08e9-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="e08e9-146">Chaque itération de la [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps de l’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="e08e9-147">Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="e08e9-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="e08e9-148">Le type de retour de la méthode iterator est <xref:System.Collections.Generic.IEnumerable%601>, un type interface itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="e08e9-149">Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.</span><span class="sxs-lookup"><span data-stu-id="e08e9-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e08e9-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="e08e9-150">Example</span></span>  
 <span data-ttu-id="e08e9-151">L'exemple suivant illustre un accesseur `Get` qui est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="e08e9-152">La déclaration de propriété comprend un `Iterator` modificateur.</span><span class="sxs-lookup"><span data-stu-id="e08e9-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="e08e9-153">Pour obtenir des exemples supplémentaires, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e08e9-153">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08e9-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e08e9-154">See Also</span></span>  
 [<span data-ttu-id="e08e9-155">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="e08e9-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="e08e9-156">Instructions</span><span class="sxs-lookup"><span data-stu-id="e08e9-156">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
