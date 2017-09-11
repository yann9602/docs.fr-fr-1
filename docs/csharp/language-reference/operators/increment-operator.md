---
title: "++, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f481dbe2437495b109d6d41cd24c8b4bb5b6a5b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="35b0d-102">++, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="35b0d-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="35b0d-103">L’opérateur d’incrément (`++`) incrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="35b0d-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="35b0d-104">L’opérateur d’incrément peut figurer avant ou après son opérande : `++variable` et `variable++`.</span><span class="sxs-lookup"><span data-stu-id="35b0d-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35b0d-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="35b0d-105">Remarks</span></span>  
 <span data-ttu-id="35b0d-106">La première forme est une opération d’incrément préfixé.</span><span class="sxs-lookup"><span data-stu-id="35b0d-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="35b0d-107">Le résultat de l’opération est la valeur de l’opérande après qu’il a été incrémenté.</span><span class="sxs-lookup"><span data-stu-id="35b0d-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="35b0d-108">La deuxième forme est une opération d’incrément suffixé.</span><span class="sxs-lookup"><span data-stu-id="35b0d-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="35b0d-109">Le résultat de l’opération est la valeur de l’opérande avant qu’il ait été incrémenté.</span><span class="sxs-lookup"><span data-stu-id="35b0d-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="35b0d-110">Les types numériques et d’énumération ont des opérateurs d’incrément prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="35b0d-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="35b0d-111">Les types définis par l’utilisateur peuvent surcharger l’opérateur `++` .</span><span class="sxs-lookup"><span data-stu-id="35b0d-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="35b0d-112">Les opérations sur les types intégraux sont en général autorisées sur l’énumération.</span><span class="sxs-lookup"><span data-stu-id="35b0d-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35b0d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="35b0d-113">Example</span></span>  
 <span data-ttu-id="35b0d-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="35b0d-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b0d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35b0d-115">See Also</span></span>  
 <span data-ttu-id="35b0d-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="35b0d-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="35b0d-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="35b0d-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="35b0d-118">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="35b0d-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

