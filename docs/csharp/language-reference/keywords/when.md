---
title: "when (référence C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
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
ms.sourcegitcommit: 9ad2eff6eb527f00ce23f463e811aa748def62d0
ms.openlocfilehash: c391c6de51d41577d61278f43d58fade5b7c139f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
 # <a name="when-c-reference"></a><span data-ttu-id="949e4-102">when (référence C#)</span><span class="sxs-lookup"><span data-stu-id="949e4-102">when (C# Reference)</span></span>

<span data-ttu-id="949e4-103">Vous pouvez utiliser le mot clé contextuel `when` pour spécifier une condition de filtre dans deux contextes :</span><span class="sxs-lookup"><span data-stu-id="949e4-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="949e4-104">dans l’instruction `catch` d’un bloc [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md) ;</span><span class="sxs-lookup"><span data-stu-id="949e4-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="949e4-105">dans l’étiquette `case` d’une instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="949e4-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="949e4-106">`when` dans une instruction `catch`</span><span class="sxs-lookup"><span data-stu-id="949e4-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="949e4-107">Depuis C# 6, `When` peut être utilisé dans une instruction `catch` pour spécifier une condition qui doit avoir la valeur True pour que le gestionnaire d’une exception spécifique soit exécuté.</span><span class="sxs-lookup"><span data-stu-id="949e4-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="949e4-108">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="949e4-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="949e4-109">où *expr* est une expression qui prend une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="949e4-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="949e4-110">Si la valeur retournée est `true`, le gestionnaire de l’exception est exécuté ; si la valeur retournée est `false`, il n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="949e4-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="949e4-111">L’exemple suivant utilise le mot clé `when` afin d’exécuter conditionnellement des gestionnaires pour une exception @System.Net.HttpRequestException selon le texte du message d’exception.</span><span class="sxs-lookup"><span data-stu-id="949e4-111">The following example uses the `when` keyword to conditionally execute handlers for an @System.Net.HttpRequestException depending on the text of the exception message.</span></span>

 <span data-ttu-id="949e4-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span><span class="sxs-lookup"><span data-stu-id="949e4-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span></span>  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="949e4-113">`when` dans une instruction `switch`</span><span class="sxs-lookup"><span data-stu-id="949e4-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="949e4-114">Depuis la version 7, les étiquettes `case` n’ont plus besoin de s’exclure mutuellement et l’ordre dans lequel les étiquettes `case` s’affichent dans une instruction `switch` peut déterminer le bloc switch exécuté.</span><span class="sxs-lookup"><span data-stu-id="949e4-114">Starting with 7, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="949e4-115">Le mot clé `when` peut être utilisé pour spécifier une condition de filtre qui fait que son étiquette case associée a la valeur True uniquement si la condition de filtre a également la valeur True.</span><span class="sxs-lookup"><span data-stu-id="949e4-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="949e4-116">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="949e4-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="949e4-117">où *expr* est un modèle de constante ou de type qui est comparé à l’expression de correspondance, et *when-condition* représente toute expression booléenne.</span><span class="sxs-lookup"><span data-stu-id="949e4-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="949e4-118">L’exemple suivant utilise le mot clé `when` pour tester les objets `Shape` ayant une superficie égale à zéro, ainsi que pour tester divers objets `Shape` ayant une superficie supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="949e4-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 <span data-ttu-id="949e4-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="949e4-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="949e4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="949e4-120">See also</span></span> 
  [<span data-ttu-id="949e4-121">switch, instruction</span><span class="sxs-lookup"><span data-stu-id="949e4-121">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="949e4-122">try/catch, instruction</span><span class="sxs-lookup"><span data-stu-id="949e4-122">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="949e4-123">try/catch/finally, instruction</span><span class="sxs-lookup"><span data-stu-id="949e4-123">try/catch/finally statement</span></span>](try-catch-finally.md) 


