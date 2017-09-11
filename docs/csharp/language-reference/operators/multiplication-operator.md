---
title: "* , opérateur (Informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
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
ms.openlocfilehash: 165ca8f797eb8d03ae1dec8c0ec5e1f4b31cb050
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="c57ba-102">*, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c57ba-102">* Operator (C# Reference)</span></span>
<span data-ttu-id="c57ba-103">L’opérateur de multiplication (`*`) calcule le produit de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="c57ba-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="c57ba-104">Par ailleurs, l’opérateur de déréférencement permet de lire un pointeur et d’écrire sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c57ba-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c57ba-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c57ba-105">Remarks</span></span>  
 <span data-ttu-id="c57ba-106">Tous les types numériques ont des opérateurs de multiplication prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c57ba-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="c57ba-107">L’opérateur `*` est aussi utilisé pour déclarer des types pointeur et déréférencer des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="c57ba-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="c57ba-108">Cet opérateur ne peut être utilisé que dans des contextes unsafe signalés par l’utilisation du mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md). Il nécessite l’option de compilateur [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c57ba-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="c57ba-109">L’opérateur de déréférencement est également appelé opérateur d’indirection.</span><span class="sxs-lookup"><span data-stu-id="c57ba-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="c57ba-110">Les types définis par l’utilisateur peuvent surcharger l’opérateur `*` binaire (voir [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c57ba-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c57ba-111">Quand un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="c57ba-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57ba-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c57ba-112">Example</span></span>  
 <span data-ttu-id="c57ba-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c57ba-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57ba-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="c57ba-114">Example</span></span>  
 <span data-ttu-id="c57ba-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c57ba-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57ba-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c57ba-116">See Also</span></span>  
 <span data-ttu-id="c57ba-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c57ba-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c57ba-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c57ba-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c57ba-119">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="c57ba-119">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="c57ba-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="c57ba-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

