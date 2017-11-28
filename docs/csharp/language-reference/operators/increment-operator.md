---
title: "++, opérateur (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c9c2c-102">++, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c9c2c-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="c9c2c-103">L’opérateur d’incrément (`++`) incrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="c9c2c-104">L’opérateur d’incrément peut figurer avant ou après son opérande : `++variable` et `variable++`.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9c2c-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9c2c-105">Remarks</span></span>  
 <span data-ttu-id="c9c2c-106">La première forme est une opération d’incrément préfixé.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="c9c2c-107">Le résultat de l’opération est la valeur de l’opérande après qu’il a été incrémenté.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="c9c2c-108">La deuxième forme est une opération d’incrément suffixé.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="c9c2c-109">Le résultat de l’opération est la valeur de l’opérande avant qu’il ait été incrémenté.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="c9c2c-110">Les types numériques et d’énumération ont des opérateurs d’incrément prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="c9c2c-111">Les types définis par l’utilisateur peuvent surcharger l’opérateur `++` .</span><span class="sxs-lookup"><span data-stu-id="c9c2c-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="c9c2c-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c9c2c-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c2c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c9c2c-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c9c2c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9c2c-114">See Also</span></span>  
 [<span data-ttu-id="c9c2c-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c9c2c-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c9c2c-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c9c2c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c9c2c-117">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="c9c2c-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
