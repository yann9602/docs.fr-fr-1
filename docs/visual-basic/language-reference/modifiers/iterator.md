---
title: "Itérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="f946a-102">Itérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f946a-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="f946a-103">Spécifie qu’une fonction ou `Get` accesseur est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="f946a-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f946a-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="f946a-104">Remarks</span></span>  
 <span data-ttu-id="f946a-105">Un *itérateur* effectue une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="f946a-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="f946a-106">Un itérateur utilise le [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instruction pour retourner chaque élément dans la collection un à la fois.</span><span class="sxs-lookup"><span data-stu-id="f946a-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="f946a-107">Lorsqu’un `Yield` instruction est atteinte, l’emplacement actuel dans le code est conservé.</span><span class="sxs-lookup"><span data-stu-id="f946a-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="f946a-108">L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.</span><span class="sxs-lookup"><span data-stu-id="f946a-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="f946a-109">Un itérateur peut être implémenté sous la forme d’une fonction ou un `Get` accesseur d’une définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="f946a-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="f946a-110">Le `Iterator` modificateur apparaît dans la déclaration de la fonction d’itérateur ou `Get` accesseur.</span><span class="sxs-lookup"><span data-stu-id="f946a-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="f946a-111">Vous appelez un itérateur depuis le code client en utilisant un [For Each... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f946a-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="f946a-112">Le type de retour d’une fonction d’itérateur ou `Get` accesseur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="f946a-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="f946a-113">Un itérateur ne peut avoir aucune `ByRef` paramètres.</span><span class="sxs-lookup"><span data-stu-id="f946a-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="f946a-114">Un itérateur ne peut pas être présent dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.</span><span class="sxs-lookup"><span data-stu-id="f946a-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="f946a-115">Un itérateur peut être une fonction anonyme.</span><span class="sxs-lookup"><span data-stu-id="f946a-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="f946a-116">Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="f946a-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="f946a-117">Pour plus d’informations sur les itérateurs, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="f946a-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f946a-118">Utilisation</span><span class="sxs-lookup"><span data-stu-id="f946a-118">Usage</span></span>  
 <span data-ttu-id="f946a-119">Le modificateur `Iterator` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="f946a-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="f946a-120">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="f946a-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="f946a-121">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="f946a-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="f946a-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="f946a-122">Example</span></span>  
 <span data-ttu-id="f946a-123">L’exemple suivant montre une fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="f946a-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="f946a-124">La fonction d’itérateur a un `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle.</span><span class="sxs-lookup"><span data-stu-id="f946a-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="f946a-125">Chaque itération de la [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps de l’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="f946a-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="f946a-126">Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="f946a-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f946a-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="f946a-127">Example</span></span>  
 <span data-ttu-id="f946a-128">L'exemple suivant illustre un accesseur `Get` qui est un itérateur.</span><span class="sxs-lookup"><span data-stu-id="f946a-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="f946a-129">Le `Iterator` modificateur est dans la déclaration de propriété.</span><span class="sxs-lookup"><span data-stu-id="f946a-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="f946a-130">Pour obtenir des exemples supplémentaires, consultez [itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="f946a-130">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f946a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f946a-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="f946a-132">Itérateurs</span><span class="sxs-lookup"><span data-stu-id="f946a-132">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="f946a-133">Yield (instruction)</span><span class="sxs-lookup"><span data-stu-id="f946a-133">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
