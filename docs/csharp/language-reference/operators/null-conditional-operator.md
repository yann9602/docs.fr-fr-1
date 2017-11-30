---
title: "?? , opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="07fa2-103">??</span><span class="sxs-lookup"><span data-stu-id="07fa2-103">??</span></span> <span data-ttu-id="07fa2-104">, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="07fa2-104">Operator (C# Reference)</span></span>
<span data-ttu-id="07fa2-105">L'opérateur `??` est appelé l'l'opérateur de fusion Null.</span><span class="sxs-lookup"><span data-stu-id="07fa2-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="07fa2-106">Il retourne l’opérande de partie gauche si ce dernier n’est pas Null ; dans le cas contraire, il retourne l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="07fa2-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07fa2-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="07fa2-107">Remarks</span></span>  
 <span data-ttu-id="07fa2-108">Un type Nullable peut représenter une valeur à partir du domaine du type, ou la valeur peut être non définie (auquel cas la valeur est Null).</span><span class="sxs-lookup"><span data-stu-id="07fa2-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="07fa2-109">Vous pouvez utiliser la `??` simplicité de syntaxe de l’opérateur pour retourner une valeur appropriée (l’opérande de droite) si l’opérande de gauche a un type nullable dont la valeur est null.</span><span class="sxs-lookup"><span data-stu-id="07fa2-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="07fa2-110">Si vous essayez d'assigner un type valeur Nullable à un type valeur non Nullable sans utiliser l'opérateur `??`, vous générez une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="07fa2-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="07fa2-111">Si vous utilisez un cast et si le type valeur Nullable est actuellement non défini, une exception `InvalidOperationException` est levée.</span><span class="sxs-lookup"><span data-stu-id="07fa2-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="07fa2-112">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="07fa2-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="07fa2-113">Le résultat d’un opérateur</span><span class="sxs-lookup"><span data-stu-id="07fa2-113">The result of a ??</span></span> <span data-ttu-id="07fa2-114">?? n’est pas considéré comme une constante même si ses deux arguments sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="07fa2-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07fa2-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="07fa2-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="07fa2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07fa2-116">See Also</span></span>  
 [<span data-ttu-id="07fa2-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="07fa2-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="07fa2-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="07fa2-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07fa2-119">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="07fa2-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="07fa2-120">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="07fa2-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="07fa2-121">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="07fa2-121">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)
