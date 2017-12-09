---
title: "explicit (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords: explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eab79d3ac48192f3c176ed44685ab58e50fc89be
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="explicit-c-reference"></a><span data-ttu-id="37eb8-102">explicit (référence C#)</span><span class="sxs-lookup"><span data-stu-id="37eb8-102">explicit (C# Reference)</span></span>
<span data-ttu-id="37eb8-103">Le mot clé `explicit` déclare un opérateur de conversion de type défini par l’utilisateur qui doit être appelé avec un cast.</span><span class="sxs-lookup"><span data-stu-id="37eb8-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="37eb8-104">Par exemple, cet opérateur effectue une conversion d’une classe nommée Fahrenheit vers une classe nommée Celsius :</span><span class="sxs-lookup"><span data-stu-id="37eb8-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 <span data-ttu-id="37eb8-105">Cet opérateur de conversion peut être appelé comme suit :</span><span class="sxs-lookup"><span data-stu-id="37eb8-105">This conversion operator can be invoked like this:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 <span data-ttu-id="37eb8-106">L’opérateur de conversion convertit un type source en type cible.</span><span class="sxs-lookup"><span data-stu-id="37eb8-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="37eb8-107">Le type source fournit l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="37eb8-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="37eb8-108">Contrairement à une conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d’un cast.</span><span class="sxs-lookup"><span data-stu-id="37eb8-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="37eb8-109">Si une opération de conversion peut provoquer des exceptions ou la perte d’informations, vous devez la marquer comme `explicit`.</span><span class="sxs-lookup"><span data-stu-id="37eb8-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="37eb8-110">Cela empêche que le compilateur appelle l’opération de conversion en mode silencieux, avec éventuellement des conséquences imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="37eb8-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="37eb8-111">L’omission du cast provoque l’erreur de compilation CS0266.</span><span class="sxs-lookup"><span data-stu-id="37eb8-111">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="37eb8-112">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="37eb8-112">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37eb8-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="37eb8-113">Example</span></span>  
 <span data-ttu-id="37eb8-114">L’exemple suivant fournit des classes `Fahrenheit` et `Celsius`, chacune fournissant un opérateur de conversion explicite à l’autre classe.</span><span class="sxs-lookup"><span data-stu-id="37eb8-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="37eb8-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="37eb8-115">Example</span></span>  
 <span data-ttu-id="37eb8-116">L’exemple suivant définit un struct, `Digit`, qui représente un seul chiffre décimal.</span><span class="sxs-lookup"><span data-stu-id="37eb8-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="37eb8-117">Un opérateur est défini pour les conversions de `byte` à `Digit`, mais étant donné que les octets ne peuvent pas tous être convertis en `Digit`, la conversion est explicite.</span><span class="sxs-lookup"><span data-stu-id="37eb8-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="37eb8-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="37eb8-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37eb8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37eb8-119">See Also</span></span>  
 [<span data-ttu-id="37eb8-120">Référence C#</span><span class="sxs-lookup"><span data-stu-id="37eb8-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="37eb8-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="37eb8-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="37eb8-122">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="37eb8-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="37eb8-123">implicit</span><span class="sxs-lookup"><span data-stu-id="37eb8-123">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="37eb8-124">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="37eb8-124">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="37eb8-125">Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="37eb8-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [<span data-ttu-id="37eb8-126">Conversions explicites définies par l’utilisateur chaînées en C#</span><span class="sxs-lookup"><span data-stu-id="37eb8-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
