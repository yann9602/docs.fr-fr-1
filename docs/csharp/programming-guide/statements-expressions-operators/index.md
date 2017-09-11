---
title: "Instructions, expressions et opérateurs (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expressions [C#]
- operators [C#]
- C# language, statements
- C# language, operators
- C# language, expressions
- statements [C#]
ms.assetid: 20f8469d-5a6a-4084-ad90-0856b7e97e45
caps.latest.revision: 22
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
ms.openlocfilehash: 71988a5b9aa59b2655b4fd7b91522fe69c8064b6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="statements-expressions-and-operators-c-programming-guide"></a><span data-ttu-id="d2a32-102">Instructions, expressions et opérateurs (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d2a32-102">Statements, Expressions, and Operators (C# Programming Guide)</span></span>
<span data-ttu-id="d2a32-103">Le code C# qui comprend une application se compose d’instructions à base de mots clés, d’expressions et d’opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d2a32-103">The C# code that comprises an application consists of statements made up of keywords, expressions and operators.</span></span> <span data-ttu-id="d2a32-104">Cette section contient des informations concernant ces éléments fondamentaux d’un programme C#.</span><span class="sxs-lookup"><span data-stu-id="d2a32-104">This section contains information regarding these fundamental elements of a C# program.</span></span>  
  
 <span data-ttu-id="d2a32-105">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="d2a32-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="d2a32-106">Instructions</span><span class="sxs-lookup"><span data-stu-id="d2a32-106">Statements</span></span>](../../../csharp/programming-guide/statements-expressions-operators/statements.md)  
  
-   [<span data-ttu-id="d2a32-107">Expressions</span><span class="sxs-lookup"><span data-stu-id="d2a32-107">Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
    -   [<span data-ttu-id="d2a32-108">Membres expression-bodied</span><span class="sxs-lookup"><span data-stu-id="d2a32-108">Expression-bodied members</span></span>](expression-bodied-members.md)
 
-   [<span data-ttu-id="d2a32-109">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="d2a32-109">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [<span data-ttu-id="d2a32-110">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="d2a32-110">Anonymous Functions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="d2a32-111">Opérateurs surchargeables</span><span class="sxs-lookup"><span data-stu-id="d2a32-111">Overloadable Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
  
-   [<span data-ttu-id="d2a32-112">Opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="d2a32-112">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
  
    -   [<span data-ttu-id="d2a32-113">Utilisation d’opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="d2a32-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
    -   [<span data-ttu-id="d2a32-114">Comment : implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="d2a32-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="d2a32-115">Comment : utiliser la surcharge d’opérateur pour créer une classe de nombres complexes</span><span class="sxs-lookup"><span data-stu-id="d2a32-115">How to: Use Operator Overloading to Create a Complex Number Class</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)  
  
-   [<span data-ttu-id="d2a32-116">Comparaisons d’égalité</span><span class="sxs-lookup"><span data-stu-id="d2a32-116">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2a32-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d2a32-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2a32-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2a32-118">See Also</span></span>  
 <span data-ttu-id="d2a32-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2a32-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d2a32-120">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="d2a32-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

