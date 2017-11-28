---
title: "Comment : effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="f72d9-102">Comment : effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f72d9-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="f72d9-103">Les objets étant polymorphes, une variable d’un type de classe de base peut contenir un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="f72d9-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="f72d9-104">Pour accéder à la méthode du type dérivé, il est nécessaire de convertir à nouveau la valeur dans le type dérivé.</span><span class="sxs-lookup"><span data-stu-id="f72d9-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="f72d9-105">Or, dans ce cas, toute tentative de conversion simple risque de lever une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="f72d9-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="f72d9-106">C’est pourquoi C# propose les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="f72d9-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="f72d9-107">Vous pouvez utiliser ces opérateurs pour vérifier si une conversion de type (cast) aboutit sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="f72d9-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="f72d9-108">En règle générale, l’opérateur `as` est plus efficace, car de fait, il ne retourne la valeur de conversion que si cette opération peut aboutir.</span><span class="sxs-lookup"><span data-stu-id="f72d9-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="f72d9-109">L’opérateur `is` retourne uniquement une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="f72d9-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="f72d9-110">Vous pouvez donc vous en servir pour déterminer simplement le type d’un objet sans avoir réellement besoin de le convertir.</span><span class="sxs-lookup"><span data-stu-id="f72d9-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72d9-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f72d9-111">Example</span></span>  
 <span data-ttu-id="f72d9-112">Les exemples suivants montrent comment utiliser les opérateurs `is` et `as` pour effectuer une conversion d’un type de référence vers un autre sans risquer de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="f72d9-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="f72d9-113">L’exemple montre aussi comment utiliser l’opérateur `as` avec les types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="f72d9-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f72d9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f72d9-114">See Also</span></span>  
 [<span data-ttu-id="f72d9-115">Types</span><span class="sxs-lookup"><span data-stu-id="f72d9-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="f72d9-116">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="f72d9-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="f72d9-117">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="f72d9-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
