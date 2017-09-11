---
title: "Modificateurs d’accès (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
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
ms.openlocfilehash: a3ad46580561500d9f011da4997007023a3bc844
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="ea8d2-102">Modificateurs d’accès (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ea8d2-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="ea8d2-103">Les modificateurs d’accès sont des mots clés utilisés pour spécifier l’accessibilité déclarée d’un membre ou d’un type.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="ea8d2-104">Cette section présente les quatre modificateurs d’accès :</span><span class="sxs-lookup"><span data-stu-id="ea8d2-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="ea8d2-105">public</span><span class="sxs-lookup"><span data-stu-id="ea8d2-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="ea8d2-106">protected</span><span class="sxs-lookup"><span data-stu-id="ea8d2-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="ea8d2-107">internal</span><span class="sxs-lookup"><span data-stu-id="ea8d2-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="ea8d2-108">private</span><span class="sxs-lookup"><span data-stu-id="ea8d2-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="ea8d2-109">Les modificateurs d’accès permettent de spécifier les cinq niveaux d’accessibilité suivants :</span><span class="sxs-lookup"><span data-stu-id="ea8d2-109">The following five accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="ea8d2-110">`public` : L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="ea8d2-111">`protected` : L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="ea8d2-112">`Internal` : L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-112">`Internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="ea8d2-113">[protected internal](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) : L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-113">[protected internal](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="ea8d2-114">`private` : L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-114">`private`: Access is limited to the containing type.</span></span>  
  
 <span data-ttu-id="ea8d2-115">Cette section introduit également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ea8d2-115">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="ea8d2-116">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) : utilisation des quatre modificateurs d’accès pour déclarer cinq niveaux d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-116">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare five levels of accessibility.</span></span>  
  
-   <span data-ttu-id="ea8d2-117">[Domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) : spécifie où, dans les sections du programme, un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-117">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="ea8d2-118">[Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) : résumé des restrictions sur l’utilisation des niveaux d’accessibilité déclarés.</span><span class="sxs-lookup"><span data-stu-id="ea8d2-118">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8d2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea8d2-119">See Also</span></span>  
 <span data-ttu-id="ea8d2-120">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea8d2-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ea8d2-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea8d2-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ea8d2-122">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea8d2-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ea8d2-123">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ea8d2-123">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="ea8d2-124">[Mots clés d’accès](../../../csharp/language-reference/keywords/access-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="ea8d2-124">[Access Keywords](../../../csharp/language-reference/keywords/access-keywords.md) </span></span>  
 [<span data-ttu-id="ea8d2-125">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="ea8d2-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

