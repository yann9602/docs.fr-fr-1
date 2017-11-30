---
title: "Modificateurs d’accès (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="0c414-102">Modificateurs d’accès (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0c414-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="0c414-103">Les modificateurs d’accès sont des mots clés utilisés pour spécifier l’accessibilité déclarée d’un membre ou d’un type.</span><span class="sxs-lookup"><span data-stu-id="0c414-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="0c414-104">Cette section présente les quatre modificateurs d’accès :</span><span class="sxs-lookup"><span data-stu-id="0c414-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="0c414-105">public</span><span class="sxs-lookup"><span data-stu-id="0c414-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="0c414-106">protected</span><span class="sxs-lookup"><span data-stu-id="0c414-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="0c414-107">internal</span><span class="sxs-lookup"><span data-stu-id="0c414-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="0c414-108">private</span><span class="sxs-lookup"><span data-stu-id="0c414-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="0c414-109">Les six niveaux d’accessibilité suivantes peuvent être spécifiées à l’aide des modificateurs d’accès :</span><span class="sxs-lookup"><span data-stu-id="0c414-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="0c414-110">`public` : L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="0c414-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="0c414-111">`protected` : L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c414-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="0c414-112">`internal` : L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="0c414-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="0c414-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): L’accès est limité à l’assembly actuel ou les types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c414-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="0c414-114">`private` : L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="0c414-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="0c414-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): L’accès est limité à la classe de conteneur ou les types dérivés de la classe de conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="0c414-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="0c414-116">Cette section introduit également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0c414-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="0c414-117">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md): à l’aide des quatre modificateurs d’accès pour déclarer des six niveaux d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="0c414-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="0c414-118">[Domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) : spécifie où, dans les sections du programme, un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="0c414-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="0c414-119">[Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) : résumé des restrictions sur l’utilisation des niveaux d’accessibilité déclarés.</span><span class="sxs-lookup"><span data-stu-id="0c414-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c414-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c414-120">See Also</span></span>  
 [<span data-ttu-id="0c414-121">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0c414-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0c414-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0c414-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0c414-123">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="0c414-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0c414-124">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="0c414-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="0c414-125">Mots clés d’accès</span><span class="sxs-lookup"><span data-stu-id="0c414-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="0c414-126">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="0c414-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
