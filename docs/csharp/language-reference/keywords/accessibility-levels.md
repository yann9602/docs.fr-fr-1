---
title: "Niveaux d’accessibilité (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="b07e0-102">Niveaux d’accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b07e0-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="b07e0-103">Utilisez les modificateurs d’accès [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md) pour spécifier l’un des niveaux d’accessibilité déclarée ci-dessous pour les membres.</span><span class="sxs-lookup"><span data-stu-id="b07e0-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="b07e0-104">Accessibilité déclarée</span><span class="sxs-lookup"><span data-stu-id="b07e0-104">Declared accessibility</span></span>|<span data-ttu-id="b07e0-105">Signification</span><span class="sxs-lookup"><span data-stu-id="b07e0-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="b07e0-106">L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="b07e0-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="b07e0-107">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="b07e0-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="b07e0-108">L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="b07e0-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="b07e0-109">L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="b07e0-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="b07e0-110">L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="b07e0-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="b07e0-111">L’accès est limité à la classe de conteneur ou les types dérivés de la classe de conteneur dans l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="b07e0-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="b07e0-112">Modificateur d’accès qu’une seule est autorisé pour un membre ou un type, sauf lorsque vous utilisez la `protected internal` ou `private protected` combinaisons.</span><span class="sxs-lookup"><span data-stu-id="b07e0-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="b07e0-113">Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b07e0-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="b07e0-114">Les espaces de noms ne présentent aucune limitation d’accès.</span><span class="sxs-lookup"><span data-stu-id="b07e0-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="b07e0-115">Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="b07e0-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="b07e0-116">Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b07e0-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="b07e0-117">Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="b07e0-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="b07e0-118">L’accessibilité par défaut de ces types est `internal`.</span><span class="sxs-lookup"><span data-stu-id="b07e0-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="b07e0-119">Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b07e0-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="b07e0-120">Membres de</span><span class="sxs-lookup"><span data-stu-id="b07e0-120">Members of</span></span>|<span data-ttu-id="b07e0-121">Accessibilité par défaut du membre</span><span class="sxs-lookup"><span data-stu-id="b07e0-121">Default member accessibility</span></span>|<span data-ttu-id="b07e0-122">Accessibilité déclarée du membre autorisée</span><span class="sxs-lookup"><span data-stu-id="b07e0-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="b07e0-123">Aucune</span><span class="sxs-lookup"><span data-stu-id="b07e0-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="b07e0-124">Aucune</span><span class="sxs-lookup"><span data-stu-id="b07e0-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="b07e0-125">L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="b07e0-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="b07e0-126">Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="b07e0-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b07e0-127">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b07e0-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b07e0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b07e0-128">See Also</span></span>  
 [<span data-ttu-id="b07e0-129">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b07e0-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b07e0-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b07e0-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b07e0-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b07e0-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b07e0-132">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="b07e0-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="b07e0-133">Domaine d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="b07e0-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="b07e0-134">Limitations sur l’utilisation des niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="b07e0-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="b07e0-135">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="b07e0-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="b07e0-136">public</span><span class="sxs-lookup"><span data-stu-id="b07e0-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="b07e0-137">private</span><span class="sxs-lookup"><span data-stu-id="b07e0-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="b07e0-138">protected</span><span class="sxs-lookup"><span data-stu-id="b07e0-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="b07e0-139">internal</span><span class="sxs-lookup"><span data-stu-id="b07e0-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
