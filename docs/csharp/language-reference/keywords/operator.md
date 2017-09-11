---
title: "operator (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
dev_langs:
- CSharp
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: 19
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
ms.openlocfilehash: 76d403493861e9c587672412cd2989c419b8717a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="operator-c-reference"></a><span data-ttu-id="28382-102">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="28382-102">operator (C# Reference)</span></span>
<span data-ttu-id="28382-103">Utilisez le mot clé `operator` pour surcharger un opérateur intégré ou pour fournir une conversion définie par l’utilisateur dans une déclaration class ou struct.</span><span class="sxs-lookup"><span data-stu-id="28382-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28382-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="28382-104">Example</span></span>  
 <span data-ttu-id="28382-105">L’exemple suivant montre une classe très simplifiée pour les nombres fractionnaires.</span><span class="sxs-lookup"><span data-stu-id="28382-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="28382-106">Cette classe surcharge les opérateurs + et * pour effectuer des opérations d’addition et de multiplication fractionnaires. Elle fournit également un opérateur de conversion qui convertit un type Fraction en type double.</span><span class="sxs-lookup"><span data-stu-id="28382-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 <span data-ttu-id="28382-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="28382-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="28382-108">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="28382-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28382-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28382-109">See Also</span></span>  
 <span data-ttu-id="28382-110">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="28382-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="28382-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="28382-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="28382-112">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="28382-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="28382-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="28382-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="28382-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="28382-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 [<span data-ttu-id="28382-115">Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="28382-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

