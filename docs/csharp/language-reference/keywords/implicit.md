---
title: "implicit (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
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
ms.openlocfilehash: e4452a3bb6da2d0d294ca26d6b957f2c1c4402fd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="implicit-c-reference"></a><span data-ttu-id="7f459-102">implicit (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7f459-102">implicit (C# Reference)</span></span>
<span data-ttu-id="7f459-103">Le mot clé `implicit` est utilisé pour déclarer un opérateur de conversion de type implicite défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7f459-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="7f459-104">Utilisez-le pour permettre les conversions implicites entre un type défini par l’utilisateur et un autre type, si la conversion n’est pas susceptible de provoquer une perte de données.</span><span class="sxs-lookup"><span data-stu-id="7f459-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f459-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="7f459-105">Example</span></span>  
 <span data-ttu-id="7f459-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7f459-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span></span>  
  
 <span data-ttu-id="7f459-107">En éliminant les casts de type superflus, les conversions implicites peuvent améliorer la lisibilité du code source.</span><span class="sxs-lookup"><span data-stu-id="7f459-107">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="7f459-108">Toutefois, étant donné que les conversions implicites ne nécessitent pas que les programmeurs castent explicitement d’un type à un autre, il faut veiller à éviter les résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="7f459-108">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="7f459-109">En général, les opérateurs de conversion implicite ne doivent jamais lever d’exceptions ni perdre d’informations pour pouvoir être utilisés en toute sécurité à l’insu du programmeur.</span><span class="sxs-lookup"><span data-stu-id="7f459-109">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="7f459-110">Si un opérateur de conversion ne peut pas répondre à ces critères, il doit être marqué comme `explicit`.</span><span class="sxs-lookup"><span data-stu-id="7f459-110">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="7f459-111">Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7f459-111">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7f459-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7f459-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f459-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f459-113">See Also</span></span>  
 <span data-ttu-id="7f459-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f459-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7f459-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f459-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7f459-116">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7f459-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="7f459-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="7f459-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 <span data-ttu-id="7f459-118">[operator (référence C#)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="7f459-118">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 [<span data-ttu-id="7f459-119">Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs</span><span class="sxs-lookup"><span data-stu-id="7f459-119">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

