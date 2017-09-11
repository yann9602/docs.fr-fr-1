---
title: "struct (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- struct_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
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
ms.openlocfilehash: 309e68a57e1ee869850d960ffaac6cf35eb6e260
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="struct-c-reference"></a><span data-ttu-id="1430f-102">struct (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="1430f-102">struct (C# Reference)</span></span>
<span data-ttu-id="1430f-103">Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire.</span><span class="sxs-lookup"><span data-stu-id="1430f-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="1430f-104">L'exemple suivant illustre une déclaration struct simple :</span><span class="sxs-lookup"><span data-stu-id="1430f-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="1430f-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="1430f-105">Remarks</span></span>  
 <span data-ttu-id="1430f-106">Les structs peuvent également contenir des [constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md), des [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), des [champs](../../../csharp/programming-guide/classes-and-structs/fields.md), des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), des [indexeurs](../../../csharp/programming-guide/indexers/index.md), des [opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md), des [événements](../../../csharp/programming-guide/events/index.md) et des [types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.</span><span class="sxs-lookup"><span data-stu-id="1430f-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="1430f-107">Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="1430f-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="1430f-108">Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct.</span><span class="sxs-lookup"><span data-stu-id="1430f-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="1430f-109">C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.</span><span class="sxs-lookup"><span data-stu-id="1430f-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="1430f-110">Pour plus d’informations, consultez [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="1430f-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1430f-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="1430f-111">Examples</span></span>  
 <span data-ttu-id="1430f-112">Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="1430f-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1430f-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1430f-113">C# Language Specification</span></span>  
 <span data-ttu-id="1430f-114">Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="1430f-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1430f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1430f-115">See Also</span></span>  
 <span data-ttu-id="1430f-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1430f-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1430f-118">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1430f-119">[Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-119">[Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md) </span></span>  
 <span data-ttu-id="1430f-120">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-120">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="1430f-121">[Types](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-121">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="1430f-122">[Types valeur](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-122">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="1430f-123">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-123">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="1430f-124">[interface](../../../csharp/language-reference/keywords/interface.md) </span><span class="sxs-lookup"><span data-stu-id="1430f-124">[interface](../../../csharp/language-reference/keywords/interface.md) </span></span>  
 [<span data-ttu-id="1430f-125">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="1430f-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)

