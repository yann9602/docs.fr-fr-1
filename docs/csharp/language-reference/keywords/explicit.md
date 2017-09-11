---
title: "explicit (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
dev_langs:
- CSharp
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
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
ms.openlocfilehash: f11a930f0be5d504c92271b66009613de5d68579
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-c-reference"></a><span data-ttu-id="c2c6d-102">explicit (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c2c6d-102">explicit (C# Reference)</span></span>
<span data-ttu-id="c2c6d-103">Le mot clé `explicit` déclare un opérateur de conversion de type défini par l’utilisateur qui doit être appelé avec un cast.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="c2c6d-104">Par exemple, cet opérateur effectue une conversion d’une classe nommée Fahrenheit vers une classe nommée Celsius :</span><span class="sxs-lookup"><span data-stu-id="c2c6d-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 <span data-ttu-id="c2c6d-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2c6d-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span></span>  
  
 <span data-ttu-id="c2c6d-106">Cet opérateur de conversion peut être appelé comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2c6d-106">This conversion operator can be invoked like this:</span></span>  
  
 <span data-ttu-id="c2c6d-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2c6d-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span></span>  
  
 <span data-ttu-id="c2c6d-108">L’opérateur de conversion convertit un type source en type cible.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-108">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="c2c6d-109">Le type source fournit l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-109">The source type provides the conversion operator.</span></span> <span data-ttu-id="c2c6d-110">Contrairement à une conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d’un cast.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-110">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="c2c6d-111">Si une opération de conversion peut provoquer des exceptions ou la perte d’informations, vous devez la marquer comme `explicit`.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-111">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="c2c6d-112">Cela empêche que le compilateur appelle l’opération de conversion en mode silencieux, avec éventuellement des conséquences imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-112">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="c2c6d-113">L’omission du cast provoque l’erreur de compilation CS0266.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-113">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="c2c6d-114">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c2c6d-114">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c6d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2c6d-115">Example</span></span>  
 <span data-ttu-id="c2c6d-116">L’exemple suivant fournit des classes `Fahrenheit` et `Celsius`, chacune fournissant un opérateur de conversion explicite à l’autre classe.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-116">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 <span data-ttu-id="c2c6d-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2c6d-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c6d-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2c6d-118">Example</span></span>  
 <span data-ttu-id="c2c6d-119">L’exemple suivant définit un struct, `Digit`, qui représente un seul chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-119">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="c2c6d-120">Un opérateur est défini pour les conversions de `byte` à `Digit`, mais étant donné que les octets ne peuvent pas tous être convertis en `Digit`, la conversion est explicite.</span><span class="sxs-lookup"><span data-stu-id="c2c6d-120">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 <span data-ttu-id="c2c6d-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2c6d-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2c6d-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c2c6d-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2c6d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2c6d-123">See Also</span></span>  
 <span data-ttu-id="c2c6d-124">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c2c6d-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c2c6d-126">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c2c6d-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="c2c6d-128">[operator (référence C#)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-128">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 <span data-ttu-id="c2c6d-129">[Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span><span class="sxs-lookup"><span data-stu-id="c2c6d-129">[How to: Implement User-Defined Conversions Between Structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span></span>  
 [<span data-ttu-id="c2c6d-130">Conversions explicites définies par l’utilisateur chaînées en C#</span><span class="sxs-lookup"><span data-stu-id="c2c6d-130">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)

