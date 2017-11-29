---
title: "as (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a><span data-ttu-id="3f50f-102">as (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3f50f-102">as (C# Reference)</span></span>
<span data-ttu-id="3f50f-103">Vous pouvez utiliser l’opérateur `as` pour effectuer certains types de conversions entre des types référence ou des [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) compatibles.</span><span class="sxs-lookup"><span data-stu-id="3f50f-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="3f50f-104">Le code suivant fournit un exemple.</span><span class="sxs-lookup"><span data-stu-id="3f50f-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="3f50f-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f50f-105">Remarks</span></span>  
 <span data-ttu-id="3f50f-106">L’opérateur `as` est semblable à une opération de cast.</span><span class="sxs-lookup"><span data-stu-id="3f50f-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="3f50f-107">Toutefois, si la conversion n’est pas possible, `as` retourne `null` au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="3f50f-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="3f50f-108">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3f50f-108">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="3f50f-109">Le code est équivalent à l’expression suivante, à la différence que la variable `expression` n’est évaluée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3f50f-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="3f50f-110">Notez que l’opérateur `as` effectue uniquement des conversions de référence, des conversions Nullable et des conversions boxing.</span><span class="sxs-lookup"><span data-stu-id="3f50f-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="3f50f-111">L’opérateur `as` ne peut pas effectuer d’autres conversions, telles que les conversions définies par l’utilisateur, qui doivent être effectuées à l’aide d’expressions cast.</span><span class="sxs-lookup"><span data-stu-id="3f50f-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f50f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f50f-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f50f-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3f50f-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f50f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f50f-114">See Also</span></span>  
 [<span data-ttu-id="3f50f-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3f50f-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3f50f-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3f50f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3f50f-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3f50f-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3f50f-118">is</span><span class="sxs-lookup"><span data-stu-id="3f50f-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="3f50f-119">?, opérateur</span><span class="sxs-lookup"><span data-stu-id="3f50f-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="3f50f-120">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="3f50f-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
