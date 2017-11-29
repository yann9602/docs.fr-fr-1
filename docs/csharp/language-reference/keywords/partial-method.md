---
title: "partielle, méthode (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: partialmethod_CSharpKeyword
helpviewer_keywords: partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03962a59d5dbe0146cad9835f81d41c06914795b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="523d3-102">partielle, méthode (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="523d3-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="523d3-103">La signature d’une méthode partielle est définie dans une partie d’un type partiel, tandis que son implémentation est définie dans une autre partie du type.</span><span class="sxs-lookup"><span data-stu-id="523d3-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="523d3-104">Les méthodes partielles permettent aux concepteurs de classes de fournir des hooks de méthode, semblables aux gestionnaires d’événements, que les développeurs peuvent décider ou non d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="523d3-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="523d3-105">Si le développeur ne fournit pas d’implémentation, le compilateur supprime la signature au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="523d3-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="523d3-106">Les méthodes partielles obéissent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="523d3-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="523d3-107">Les signatures des deux parties du type partiel doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="523d3-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="523d3-108">La méthode doit retourner void.</span><span class="sxs-lookup"><span data-stu-id="523d3-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="523d3-109">Aucun modificateur d’accès n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="523d3-109">No access modifiers are allowed.</span></span> <span data-ttu-id="523d3-110">Les méthodes partielles sont implicitement privées.</span><span class="sxs-lookup"><span data-stu-id="523d3-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="523d3-111">L’exemple suivant illustre une méthode partielle définie dans deux parties d’une classe partielle :</span><span class="sxs-lookup"><span data-stu-id="523d3-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="523d3-112">Pour plus d’informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="523d3-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523d3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="523d3-113">See Also</span></span>  
 [<span data-ttu-id="523d3-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="523d3-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="523d3-115">partial (type)</span><span class="sxs-lookup"><span data-stu-id="523d3-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
