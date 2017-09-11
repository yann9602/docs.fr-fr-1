---
title: "as (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
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
ms.openlocfilehash: 7a55c696ac295eee8d5d35ed56038f3c4a90b215
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="as-c-reference"></a><span data-ttu-id="4289d-102">as (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4289d-102">as (C# Reference)</span></span>
<span data-ttu-id="4289d-103">Vous pouvez utiliser l’opérateur `as` pour effectuer certains types de conversions entre des types référence ou des [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) compatibles.</span><span class="sxs-lookup"><span data-stu-id="4289d-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="4289d-104">Le code suivant fournit un exemple.</span><span class="sxs-lookup"><span data-stu-id="4289d-104">The following code shows an example.</span></span>  
  
 <span data-ttu-id="4289d-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4289d-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4289d-106">Notes</span><span class="sxs-lookup"><span data-stu-id="4289d-106">Remarks</span></span>  
 <span data-ttu-id="4289d-107">L’opérateur `as` est semblable à une opération de cast.</span><span class="sxs-lookup"><span data-stu-id="4289d-107">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="4289d-108">Toutefois, si la conversion n’est pas possible, `as` retourne `null` au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="4289d-108">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="4289d-109">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4289d-109">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="4289d-110">Le code est équivalent à l’expression suivante, à la différence que la variable `expression` n’est évaluée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="4289d-110">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="4289d-111">Notez que l’opérateur `as` effectue uniquement des conversions de référence, des conversions Nullable et des conversions boxing.</span><span class="sxs-lookup"><span data-stu-id="4289d-111">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="4289d-112">L’opérateur `as` ne peut pas effectuer d’autres conversions, telles que les conversions définies par l’utilisateur, qui doivent être effectuées à l’aide d’expressions cast.</span><span class="sxs-lookup"><span data-stu-id="4289d-112">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4289d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="4289d-113">Example</span></span>  
 <span data-ttu-id="4289d-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4289d-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4289d-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4289d-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4289d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4289d-116">See Also</span></span>  
 <span data-ttu-id="4289d-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4289d-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4289d-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4289d-120">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-120">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="4289d-121">[?, opérateur](../../../csharp/language-reference/operators/conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="4289d-121">[?: Operator](../../../csharp/language-reference/operators/conditional-operator.md) </span></span>  
 [<span data-ttu-id="4289d-122">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="4289d-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

