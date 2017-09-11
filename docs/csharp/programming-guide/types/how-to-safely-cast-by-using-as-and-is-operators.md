---
title: "Guide pratique pour effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
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
ms.openlocfilehash: c5daa8525f45c123dabb0f59dfd29385b9e50354
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="d8e18-102">Guide pratique pour effectuer sans risque un cast à l'aide des opérateurs as et is (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d8e18-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="d8e18-103">Les objets étant polymorphes, une variable d’un type de classe de base peut contenir un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="d8e18-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="d8e18-104">Pour accéder à la méthode du type dérivé, il est nécessaire de convertir à nouveau la valeur dans le type dérivé.</span><span class="sxs-lookup"><span data-stu-id="d8e18-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="d8e18-105">Or, dans ce cas, toute tentative de conversion simple risque de lever une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="d8e18-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="d8e18-106">C’est pourquoi C# propose les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="d8e18-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="d8e18-107">Vous pouvez utiliser ces opérateurs pour vérifier si une conversion de type (cast) aboutit sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="d8e18-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="d8e18-108">En règle générale, l’opérateur `as` est plus efficace, car de fait, il ne retourne la valeur de conversion que si cette opération peut aboutir.</span><span class="sxs-lookup"><span data-stu-id="d8e18-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="d8e18-109">L’opérateur `is` retourne uniquement une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="d8e18-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="d8e18-110">Vous pouvez donc vous en servir pour déterminer simplement le type d’un objet sans avoir réellement besoin de le convertir.</span><span class="sxs-lookup"><span data-stu-id="d8e18-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8e18-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8e18-111">Example</span></span>  
 <span data-ttu-id="d8e18-112">Les exemples suivants montrent comment utiliser les opérateurs `is` et `as` pour effectuer une conversion d’un type de référence vers un autre sans risquer de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="d8e18-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="d8e18-113">L’exemple montre aussi comment utiliser l’opérateur `as` avec les types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="d8e18-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 <span data-ttu-id="d8e18-114">[!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d8e18-114">[!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e18-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8e18-115">See Also</span></span>  
 <span data-ttu-id="d8e18-116">[Types](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8e18-116">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="d8e18-117">[Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="d8e18-117">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 [<span data-ttu-id="d8e18-118">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="d8e18-118">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)

