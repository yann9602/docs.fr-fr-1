---
title: "new, opérateur (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
ms.openlocfilehash: 59e1cc2006548df9a7a10283a34044040e5c2fef
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="new-operator-c-reference"></a><span data-ttu-id="58446-102">new, opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="58446-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="58446-103">Cet opérateur s’utilise pour créer des objets et appeler des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="58446-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="58446-104">Exemple :</span><span class="sxs-lookup"><span data-stu-id="58446-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="58446-105">Il est également utilisé pour créer des instances de types anonymes :</span><span class="sxs-lookup"><span data-stu-id="58446-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="58446-106">L’opérateur `new` est aussi utilisé pour appeler le constructeur par défaut pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="58446-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="58446-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="58446-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="58446-108">Dans l’instruction précédente, `i` est initialisé à `0`, qui est la valeur par défaut pour le type `int`.</span><span class="sxs-lookup"><span data-stu-id="58446-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="58446-109">L’instruction produit le même résultat que ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="58446-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="58446-110">Pour obtenir une liste complète des valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="58446-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="58446-111">N’oubliez pas qu’il est incorrect de déclarer un constructeur par défaut pour un [struct](../../../csharp/language-reference/keywords/struct.md), car chaque type valeur a implicitement un constructeur public par défaut.</span><span class="sxs-lookup"><span data-stu-id="58446-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="58446-112">Il est possible de déclarer des constructeurs paramétrables sur un type struct pour définir ses valeurs initiales, mais cela est nécessaire uniquement si d’autres valeurs que la valeur par défaut sont requises.</span><span class="sxs-lookup"><span data-stu-id="58446-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="58446-113">Les objets de type valeur tels que les structs sont créés sur la pile, tandis que les objets de type référence tels que les classes sont créés sur le tas.</span><span class="sxs-lookup"><span data-stu-id="58446-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="58446-114">Les deux types d’objets sont détruits automatiquement, mais les objets basés sur des types valeur sont détruits quand ils sortent de la portée, alors que les objets basés sur des types référence sont détruits à n’importe quel moment après la suppression de la dernière référence à ces objets.</span><span class="sxs-lookup"><span data-stu-id="58446-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="58446-115">Pour les types référence qui consomment des ressources fixes telles que de grandes quantités de mémoire, des descripteurs de fichiers ou des connexions réseau, il est parfois préférable d’utiliser la finalisation déterministe pour s’assurer que l’objet est détruit dès que possible.</span><span class="sxs-lookup"><span data-stu-id="58446-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="58446-116">Pour plus d’informations, consultez [using, instruction](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58446-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="58446-117">L’opérateur `new` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="58446-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="58446-118">Si l’opérateur `new` ne réussit pas à allouer de la mémoire, il lève l’exception <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="58446-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58446-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="58446-119">Example</span></span>  
 <span data-ttu-id="58446-120">Dans l’exemple suivant, un objet `struct` et un objet de classe sont créés et initialisés à l’aide de l’opérateur `new`, puis des valeurs leur sont assignées.</span><span class="sxs-lookup"><span data-stu-id="58446-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="58446-121">La valeur par défaut et les valeurs assignées sont affichées.</span><span class="sxs-lookup"><span data-stu-id="58446-121">The default and the assigned values are displayed.</span></span>  
  
 <span data-ttu-id="58446-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="58446-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="58446-123">Notez que, dans l’exemple, la valeur par défaut d’une chaîne est `null`.</span><span class="sxs-lookup"><span data-stu-id="58446-123">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="58446-124">Elle n’est donc pas affichée.</span><span class="sxs-lookup"><span data-stu-id="58446-124">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="58446-125">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="58446-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58446-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58446-126">See Also</span></span>  
 <span data-ttu-id="58446-127">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="58446-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="58446-128">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="58446-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="58446-129">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="58446-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="58446-130">[Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="58446-130">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 <span data-ttu-id="58446-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="58446-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="58446-132">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="58446-132">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

