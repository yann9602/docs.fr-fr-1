---
title: "partielle, méthode (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
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
ms.openlocfilehash: b6f8ecca01ebf681c906b73abefc94e9e45b8700
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="partial-method-c-reference"></a><span data-ttu-id="92ece-102">partielle, méthode (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="92ece-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="92ece-103">La signature d’une méthode partielle est définie dans une partie d’un type partiel, tandis que son implémentation est définie dans une autre partie du type.</span><span class="sxs-lookup"><span data-stu-id="92ece-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="92ece-104">Les méthodes partielles permettent aux concepteurs de classes de fournir des hooks de méthode, semblables aux gestionnaires d’événements, que les développeurs peuvent décider ou non d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="92ece-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="92ece-105">Si le développeur ne fournit pas d’implémentation, le compilateur supprime la signature au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="92ece-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="92ece-106">Les méthodes partielles obéissent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="92ece-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="92ece-107">Les signatures des deux parties du type partiel doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="92ece-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="92ece-108">La méthode doit retourner void.</span><span class="sxs-lookup"><span data-stu-id="92ece-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="92ece-109">Aucun modificateur d’accès n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="92ece-109">No access modifiers are allowed.</span></span> <span data-ttu-id="92ece-110">Les méthodes partielles sont implicitement privées.</span><span class="sxs-lookup"><span data-stu-id="92ece-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="92ece-111">L’exemple suivant illustre une méthode partielle définie dans deux parties d’une classe partielle :</span><span class="sxs-lookup"><span data-stu-id="92ece-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 <span data-ttu-id="92ece-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="92ece-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span></span>  
  
 <span data-ttu-id="92ece-113">Pour plus d’informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="92ece-113">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ece-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92ece-114">See Also</span></span>  
 <span data-ttu-id="92ece-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="92ece-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="92ece-116">partial (type)</span><span class="sxs-lookup"><span data-stu-id="92ece-116">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)

