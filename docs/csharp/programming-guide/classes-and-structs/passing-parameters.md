---
title: "Passage de paramètres (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
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
ms.openlocfilehash: 4b8c0c7f7b8c3820edbafbe90fb961c12da8fc84
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="6bbb3-102">Passage de paramètres (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6bbb3-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="6bbb3-103">En C#, les arguments peuvent être passés aux paramètres par valeur ou par référence.</span><span class="sxs-lookup"><span data-stu-id="6bbb3-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="6bbb3-104">Avec le passage par référence, les fonctions membres, les méthodes, les propriétés, les indexeurs, les opérateurs et les constructeurs peuvent changer la valeur des paramètres et rendre cette modification persistante dans l’environnement d’appel.</span><span class="sxs-lookup"><span data-stu-id="6bbb3-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="6bbb3-105">Pour passer un paramètre par référence, utilisez le mot clé `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="6bbb3-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="6bbb3-106">Pour plus de simplicité, les exemples de cette rubrique utilisent uniquement le mot clé `ref`.</span><span class="sxs-lookup"><span data-stu-id="6bbb3-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="6bbb3-107">Pour plus d’informations sur la différence entre `ref` et `out`, consultez [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md) et [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="6bbb3-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="6bbb3-108">L’exemple suivant illustre la différence entre les paramètres de référence et de valeur.</span><span class="sxs-lookup"><span data-stu-id="6bbb3-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 <span data-ttu-id="6bbb3-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6bbb3-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="6bbb3-110">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bbb3-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6bbb3-111">Passage de paramètres de type valeur</span><span class="sxs-lookup"><span data-stu-id="6bbb3-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="6bbb3-112">Passage de paramètres de type référence</span><span class="sxs-lookup"><span data-stu-id="6bbb3-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6bbb3-113">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6bbb3-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6bbb3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bbb3-114">See Also</span></span>  
 <span data-ttu-id="6bbb3-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6bbb3-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="6bbb3-116">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6bbb3-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

