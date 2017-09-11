---
title: "let, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
dev_langs:
- CSharp
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
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
ms.openlocfilehash: 37ec0cb0c8c374a0b5250d82e880c96696b5584a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="let-clause-c-reference"></a><span data-ttu-id="321b1-102">let, clause (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="321b1-102">let clause (C# Reference)</span></span>
<span data-ttu-id="321b1-103">Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures.</span><span class="sxs-lookup"><span data-stu-id="321b1-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="321b1-104">Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="321b1-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="321b1-105">Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="321b1-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="321b1-106">Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.</span><span class="sxs-lookup"><span data-stu-id="321b1-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="321b1-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="321b1-107">Example</span></span>  
 <span data-ttu-id="321b1-108">Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :</span><span class="sxs-lookup"><span data-stu-id="321b1-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="321b1-109">Pour créer un type énumérable qui peut lui-même être interrogé.</span><span class="sxs-lookup"><span data-stu-id="321b1-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="321b1-110">Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`.</span><span class="sxs-lookup"><span data-stu-id="321b1-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="321b1-111">Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="321b1-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 <span data-ttu-id="321b1-112">[!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="321b1-112">[!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321b1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="321b1-113">See Also</span></span>  
 <span data-ttu-id="321b1-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="321b1-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="321b1-115">[Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="321b1-115">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="321b1-116">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="321b1-116">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="321b1-117">[Bien démarrer avec LINQ en C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="321b1-117">[Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 [<span data-ttu-id="321b1-118">Guide pratique pour gérer des exceptions dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="321b1-118">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)

