---
title: "Passage de paramètres (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="6136e-102">Passage de paramètres (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6136e-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="6136e-103">En C#, les arguments peuvent être passés aux paramètres par valeur ou par référence.</span><span class="sxs-lookup"><span data-stu-id="6136e-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="6136e-104">Avec le passage par référence, les fonctions membres, les méthodes, les propriétés, les indexeurs, les opérateurs et les constructeurs peuvent changer la valeur des paramètres et rendre cette modification persistante dans l’environnement d’appel.</span><span class="sxs-lookup"><span data-stu-id="6136e-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="6136e-105">Pour passer un paramètre par référence, utilisez le mot clé `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="6136e-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="6136e-106">Pour plus de simplicité, les exemples de cette rubrique utilisent uniquement le mot clé `ref`.</span><span class="sxs-lookup"><span data-stu-id="6136e-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="6136e-107">Pour plus d’informations sur la différence entre `ref` et `out`, consultez [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md) et [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="6136e-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="6136e-108">L’exemple suivant illustre la différence entre les paramètres de référence et de valeur.</span><span class="sxs-lookup"><span data-stu-id="6136e-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="6136e-109">Pour plus d’informations, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6136e-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6136e-110">Passage de paramètres de type valeur</span><span class="sxs-lookup"><span data-stu-id="6136e-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="6136e-111">Passage de paramètres de type référence</span><span class="sxs-lookup"><span data-stu-id="6136e-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6136e-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6136e-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6136e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6136e-113">See Also</span></span>  
 [<span data-ttu-id="6136e-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6136e-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6136e-115">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6136e-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
