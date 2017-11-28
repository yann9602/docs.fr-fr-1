---
title: "struct (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a><span data-ttu-id="796fa-102">struct (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="796fa-102">struct (C# Reference)</span></span>
<span data-ttu-id="796fa-103">Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire.</span><span class="sxs-lookup"><span data-stu-id="796fa-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="796fa-104">L'exemple suivant illustre une déclaration struct simple :</span><span class="sxs-lookup"><span data-stu-id="796fa-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="796fa-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="796fa-105">Remarks</span></span>  
 <span data-ttu-id="796fa-106">Les structs peuvent également contenir des [constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md), des [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), des [champs](../../../csharp/programming-guide/classes-and-structs/fields.md), des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), des [indexeurs](../../../csharp/programming-guide/indexers/index.md), des [opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md), des [événements](../../../csharp/programming-guide/events/index.md) et des [types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md). Toutefois, si plusieurs membres sont nécessaires, il est conseillé de plutôt utiliser une classe.</span><span class="sxs-lookup"><span data-stu-id="796fa-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="796fa-107">Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="796fa-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="796fa-108">Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct.</span><span class="sxs-lookup"><span data-stu-id="796fa-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="796fa-109">C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.</span><span class="sxs-lookup"><span data-stu-id="796fa-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="796fa-110">Pour plus d’informations, consultez [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="796fa-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="796fa-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="796fa-111">Examples</span></span>  
 <span data-ttu-id="796fa-112">Pour obtenir des exemples et des informations supplémentaires, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="796fa-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="796fa-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="796fa-113">C# Language Specification</span></span>  
 <span data-ttu-id="796fa-114">Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="796fa-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796fa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="796fa-115">See Also</span></span>  
 [<span data-ttu-id="796fa-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="796fa-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="796fa-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="796fa-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="796fa-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="796fa-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="796fa-119">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="796fa-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="796fa-120">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="796fa-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="796fa-121">Types</span><span class="sxs-lookup"><span data-stu-id="796fa-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="796fa-122">Types valeur</span><span class="sxs-lookup"><span data-stu-id="796fa-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="796fa-123">class</span><span class="sxs-lookup"><span data-stu-id="796fa-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="796fa-124">interface</span><span class="sxs-lookup"><span data-stu-id="796fa-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="796fa-125">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="796fa-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
