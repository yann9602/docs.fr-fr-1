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
ms.openlocfilehash: 6c2372380d8162d3e7760bba4a43cdb1c568bf5b
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="21e22-103">??</span><span class="sxs-lookup"><span data-stu-id="21e22-103">??</span></span> <span data-ttu-id="21e22-104">, opérateur (Informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="21e22-104">Operator (C# Reference)</span></span>
<span data-ttu-id="21e22-105">L'opérateur `??` est appelé l'l'opérateur de fusion Null.</span><span class="sxs-lookup"><span data-stu-id="21e22-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="21e22-106">Il retourne l’opérande de partie gauche si ce dernier n’est pas Null ; dans le cas contraire, il retourne l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="21e22-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e22-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="21e22-107">Remarks</span></span>  
 <span data-ttu-id="21e22-108">Un type Nullable peut représenter une valeur à partir du domaine du type, ou la valeur peut être non définie (auquel cas la valeur est Null).</span><span class="sxs-lookup"><span data-stu-id="21e22-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="21e22-109">Utilisez la simplicité de syntaxe de l’opérateur `??` pour retourner une valeur appropriée (l’opérande de partie droite) si l’opérande de partie gauche a un type Nullable dont la valeur est Null.</span><span class="sxs-lookup"><span data-stu-id="21e22-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="21e22-110">Si vous essayez d'assigner un type valeur Nullable à un type valeur non Nullable sans utiliser l'opérateur `??`, vous générez une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="21e22-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="21e22-111">Si vous utilisez un cast et si le type valeur Nullable est actuellement non défini, une exception `InvalidOperationException` est levée.</span><span class="sxs-lookup"><span data-stu-id="21e22-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="21e22-112">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="21e22-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="21e22-113">Le résultat d’un opérateur</span><span class="sxs-lookup"><span data-stu-id="21e22-113">The result of a ??</span></span> <span data-ttu-id="21e22-114">?? n’est pas considéré comme une constante même si ses deux arguments sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="21e22-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e22-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="21e22-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="21e22-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21e22-116">See Also</span></span>  
 [<span data-ttu-id="21e22-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="21e22-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="21e22-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="21e22-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="21e22-119">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="21e22-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="21e22-120">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="21e22-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="21e22-121">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="21e22-121">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
