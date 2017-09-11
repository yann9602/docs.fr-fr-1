---
title: "Comparaisons d'égalité (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
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
ms.openlocfilehash: 948bbc1b5b8535cc31ea362497fa69a816b43edc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="dc8cb-102">Comparaisons d'égalité (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="dc8cb-102">Equality Comparisons (C# Programming Guide)</span></span>
<span data-ttu-id="dc8cb-103">Il est parfois nécessaire de comparer l’égalité de deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-103">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="dc8cb-104">Dans certains cas, vous testez *l’égalité de valeur*, également appelée *équivalence*, qui signifie que les valeurs contenues dans les deux variables sont égales.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-104">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="dc8cb-105">Dans d’autres cas, vous devez déterminer si deux variables référencent le même objet sous-jacent en mémoire.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-105">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="dc8cb-106">Ce type d’égalité est appelée *l’égalité de référence* ou *identité*.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-106">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="dc8cb-107">Cette rubrique décrit ces deux genres d’égalité et fournit des liens vers d’autres rubriques pour obtenir plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-107">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="dc8cb-108">Égalité de référence</span><span class="sxs-lookup"><span data-stu-id="dc8cb-108">Reference Equality</span></span>  
 <span data-ttu-id="dc8cb-109">L’égalité de références signifie que deux références d’objets référencent le même objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-109">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="dc8cb-110">Cela peut se produire par simple assignation, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-110">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc8cb-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc8cb-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span></span>  
  
 <span data-ttu-id="dc8cb-112">Dans ce code, deux objets sont créés, mais après l’instruction d’assignation, les deux références référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-112">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="dc8cb-113">Elles présentent donc une égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-113">Therefore they have reference equality.</span></span> <span data-ttu-id="dc8cb-114">Utilisez la méthode <xref:System.Object.ReferenceEquals%2A> pour déterminer si deux références référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-114">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
 <span data-ttu-id="dc8cb-115">Le concept d’égalité de référence s’applique uniquement aux types référence.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-115">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="dc8cb-116">Les objets de type valeur ne peuvent pas avoir une égalité de référence, car quand une instance d’un type valeur est assignée à une variable, une copie de la valeur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-116">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="dc8cb-117">Ainsi, vous ne pouvez jamais avoir deux structs unboxed qui référencent le même emplacement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-117">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="dc8cb-118">De plus, si vous utilisez <xref:System.Object.ReferenceEquals%2A> pour comparer deux types valeur, le résultat est toujours `false`, même si les valeurs contenues dans les objets sont toutes identiques.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-118">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="dc8cb-119">Cela est dû au fait que chaque variable est convertie en une instance d’objet distincte.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-119">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="dc8cb-120">Pour plus d’informations, consultez [Guide pratique pour tester l’égalité des références (identité)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span><span class="sxs-lookup"><span data-stu-id="dc8cb-120">For more information, see [How to: Test for Reference Equality (Identity)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>  
  
## <a name="value-equality"></a><span data-ttu-id="dc8cb-121">Égalité de valeur</span><span class="sxs-lookup"><span data-stu-id="dc8cb-121">Value Equality</span></span>  
 <span data-ttu-id="dc8cb-122">L’égalité de valeur signifie que deux objets contiennent les mêmes valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-122">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="dc8cb-123">Pour les types valeur primitifs tels que [int](../../../csharp/language-reference/keywords/int.md) ou [bool](../../../csharp/language-reference/keywords/bool.md), les tests d’égalité de valeur sont simples.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-123">For primitive value types such as [int](../../../csharp/language-reference/keywords/int.md) or [bool](../../../csharp/language-reference/keywords/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="dc8cb-124">Vous pouvez utiliser l’opérateur [==](../../../csharp/language-reference/operators/equality-comparison-operator.md), comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-124">You can use the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="dc8cb-125">Pour la plupart des autres types, les tests d’égalité de valeur sont plus complexes parce qu’ils vous demandent de comprendre comment le type la définit.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-125">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="dc8cb-126">Pour les classes et structs qui ont plusieurs champs ou propriétés, l’égalité de valeur signifie souvent que tous les champs ou propriétés ont la même valeur.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-126">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="dc8cb-127">Par exemple, deux objets `Point` peuvent être définis comme équivalents si pointA.X est égal à pointB.X et que pointA.Y est égal à pointB.Y.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-127">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
 <span data-ttu-id="dc8cb-128">Toutefois, il n’est pas obligatoire que l’équivalence soit basée sur tous les champs dans un type.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-128">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="dc8cb-129">Elle peut être basée sur une partie.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-129">It can be based on a subset.</span></span> <span data-ttu-id="dc8cb-130">Quand vous comparez des types dont vous n’êtes pas propriétaire, vous devez bien comprendre comment l’équivalence est définie pour ce type.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-130">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="dc8cb-131">Pour plus d’informations sur la façon de définir l’égalité de valeur dans vos propres classes et structs, consultez [Guide pratique pour définir une égalité de valeurs pour un type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span><span class="sxs-lookup"><span data-stu-id="dc8cb-131">For more information about how to define value equality in your own classes and structs, see [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>  
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="dc8cb-132">Égalité de valeur pour les valeurs à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="dc8cb-132">Value Equality for Floating Point Values</span></span>  
 <span data-ttu-id="dc8cb-133">Les comparaisons d’égalité des valeurs à virgule flottante ([double](../../../csharp/language-reference/keywords/double.md) et [float](../../../csharp/language-reference/keywords/float.md)) sont problématiques en raison de l’imprécision de l’arithmétique à virgule flottante sur les ordinateurs binaires.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-133">Equality comparisons of floating point values ([double](../../../csharp/language-reference/keywords/double.md) and [float](../../../csharp/language-reference/keywords/float.md)) are problematic because of the imprecision of floating point arithmetic on binary computers.</span></span> <span data-ttu-id="dc8cb-134">Pour plus d’informations, consultez les notes dans la rubrique <xref:System.Double?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-134">For more information, see the remarks in the topic <xref:System.Double?displayProperty=fullName>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="dc8cb-135">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="dc8cb-135">Related Topics</span></span>  
  
|<span data-ttu-id="dc8cb-136">Titre</span><span class="sxs-lookup"><span data-stu-id="dc8cb-136">Title</span></span>|<span data-ttu-id="dc8cb-137">Description</span><span class="sxs-lookup"><span data-stu-id="dc8cb-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dc8cb-138">Guide pratique pour tester l’égalité des références (Identité)</span><span class="sxs-lookup"><span data-stu-id="dc8cb-138">How to: Test for Reference Equality (Identity)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="dc8cb-139">Décrit comment déterminer si deux variables présentent une égalité de référence.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-139">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="dc8cb-140">Guide pratique pour définir une égalité de valeurs pour un type</span><span class="sxs-lookup"><span data-stu-id="dc8cb-140">How to: Define Value Equality for a Type</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="dc8cb-141">Décrit comment fournir une définition personnalisée de l’égalité de valeur pour un type.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-141">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="dc8cb-142">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="dc8cb-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)|<span data-ttu-id="dc8cb-143">Fournit des liens vers des informations détaillées sur les fonctionnalités et les fonctions clés du langage C# disponibles en C# par l’intermédiaire du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-143">Provides links to detailed information about important C# language features and features that are available to C# through the .NET Framework.</span></span>|  
|[<span data-ttu-id="dc8cb-144">Types</span><span class="sxs-lookup"><span data-stu-id="dc8cb-144">Types</span></span>](../../../csharp/programming-guide/types/index.md)|<span data-ttu-id="dc8cb-145">Fournit des informations sur le système de typeC# et des liens vers des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="dc8cb-145">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc8cb-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc8cb-146">See Also</span></span>  
 [<span data-ttu-id="dc8cb-147">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="dc8cb-147">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

