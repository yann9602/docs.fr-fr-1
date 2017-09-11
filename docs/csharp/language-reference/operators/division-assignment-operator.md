---
title: "/=, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
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
ms.openlocfilehash: 5e105bf11f5413d77d62be4177ed22ba420312c3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="2e720-102">/=, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2e720-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="2e720-103">Opérateur d’assignation de division.</span><span class="sxs-lookup"><span data-stu-id="2e720-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e720-104">Notes</span><span class="sxs-lookup"><span data-stu-id="2e720-104">Remarks</span></span>  
 <span data-ttu-id="2e720-105">Une expression qui utilise l’opérateur d’assignation `/=`, telle que</span><span class="sxs-lookup"><span data-stu-id="2e720-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="2e720-106">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="2e720-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="2e720-107">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="2e720-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="2e720-108">L’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) est prédéfini pour les types numériques afin d’effectuer une division.</span><span class="sxs-lookup"><span data-stu-id="2e720-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="2e720-109">Vous ne pouvez pas surcharger directement l’opérateur `/=`, mais les types définis par l’utilisateur peuvent surcharger l’[opérateur /](../../../csharp/language-reference/operators/division-operator.md) (voir [opérateur](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2e720-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2e720-110">Sur tous les opérateurs d’assignation composée, le fait de surcharger l’opérateur binaire surcharge implicitement l’assignation composée équivalente.</span><span class="sxs-lookup"><span data-stu-id="2e720-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e720-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e720-111">Example</span></span>  
 <span data-ttu-id="2e720-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e720-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e720-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e720-113">See Also</span></span>  
 <span data-ttu-id="2e720-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2e720-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2e720-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2e720-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2e720-116">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="2e720-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

