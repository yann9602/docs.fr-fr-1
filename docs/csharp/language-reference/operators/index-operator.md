---
title: "[], opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
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
ms.openlocfilehash: b49d41af0dd4dc34b1b74c62ce8779aa31d69f77
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="9a7d8-102">[], opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9a7d8-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="9a7d8-103">Les crochets (`[]`) sont utilisés pour les tableaux, les indexeurs et les attributs.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="9a7d8-104">Ils peuvent également être utilisés avec les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a7d8-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a7d8-105">Remarks</span></span>  
 <span data-ttu-id="9a7d8-106">Un type tableau est un type suivi de `[]` :</span><span class="sxs-lookup"><span data-stu-id="9a7d8-106">An array type is a type followed by `[]`:</span></span>  
  
 <span data-ttu-id="9a7d8-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a7d8-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="9a7d8-108">Pour accéder à un élément d’un tableau, vous devez placer l’index de l’élément souhaité entre crochets :</span><span class="sxs-lookup"><span data-stu-id="9a7d8-108">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 <span data-ttu-id="9a7d8-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a7d8-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="9a7d8-110">Une exception est levée si un index de tableau est hors portée.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-110">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="9a7d8-111">L’opérateur d’indexation de tableau ne peut pas être surchargé. Toutefois, les types peuvent définir les indexeurs, ainsi que les propriétés qui acceptent un ou plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-111">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="9a7d8-112">Les paramètres d’indexeur sont placés entre crochets, comme les index de tableau, mais ils peuvent être déclarés comme étant de tout type, contrairement aux index de tableau, qui doivent être intégraux.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-112">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="9a7d8-113">Par exemple, le .NET Framework définit un type `Hashtable` qui associe des clés et des valeurs de type arbitraire :</span><span class="sxs-lookup"><span data-stu-id="9a7d8-113">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 <span data-ttu-id="9a7d8-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a7d8-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="9a7d8-115">Les crochets sont également utilisés pour spécifier des [attributs](../../../csharp/programming-guide/concepts/attributes/index.md) :</span><span class="sxs-lookup"><span data-stu-id="9a7d8-115">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 <span data-ttu-id="9a7d8-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a7d8-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="9a7d8-117">Vous pouvez utiliser des crochets pour indexer un pointeur :</span><span class="sxs-lookup"><span data-stu-id="9a7d8-117">You can use square brackets to index off a pointer:</span></span>  
  
 <span data-ttu-id="9a7d8-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a7d8-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="9a7d8-119">Aucune vérification des limites n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="9a7d8-119">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9a7d8-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9a7d8-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a7d8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a7d8-121">See Also</span></span>  
 <span data-ttu-id="9a7d8-122">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9a7d8-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9a7d8-124">[Opérateurs C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-124">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="9a7d8-125">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-125">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="9a7d8-126">[Indexeurs](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-126">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="9a7d8-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d8-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="9a7d8-128">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="9a7d8-128">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)

