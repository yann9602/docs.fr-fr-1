---
title: "Niveaux d’accessibilité (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
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
ms.openlocfilehash: 796802a407c486c1df5332d5b4920467f3a1171b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="dc0c4-102">Niveaux d’accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dc0c4-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="dc0c4-103">Utilisez les modificateurs d’accès [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md) pour spécifier l’un des niveaux d’accessibilité déclarée ci-dessous pour les membres.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="dc0c4-104">Accessibilité déclarée</span><span class="sxs-lookup"><span data-stu-id="dc0c4-104">Declared accessibility</span></span>|<span data-ttu-id="dc0c4-105">Signification</span><span class="sxs-lookup"><span data-stu-id="dc0c4-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="dc0c4-106">L’accès n’est pas limité.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="dc0c4-107">L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="dc0c4-108">L’accès est limité à l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="dc0c4-109">L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="dc0c4-110">L’accès est limité au type conteneur.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-110">Access is limited to the containing type.</span></span>|  
  
 <span data-ttu-id="dc0c4-111">Vous ne pouvez spécifier qu’un seul modificateur d’accès pour un membre ou un type, sauf si vous utilisez la combinaison `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-111">Only one access modifier is allowed for a member or type, except when you use the `protected internal` combination.</span></span>  
  
 <span data-ttu-id="dc0c4-112">Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-112">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="dc0c4-113">Les espaces de noms ne présentent aucune limitation d’accès.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-113">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="dc0c4-114">Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-114">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="dc0c4-115">Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-115">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="dc0c4-116">Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-116">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="dc0c4-117">L’accessibilité par défaut de ces types est `internal`.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-117">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="dc0c4-118">Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-118">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="dc0c4-119">Membres de</span><span class="sxs-lookup"><span data-stu-id="dc0c4-119">Members of</span></span>|<span data-ttu-id="dc0c4-120">Accessibilité par défaut du membre</span><span class="sxs-lookup"><span data-stu-id="dc0c4-120">Default member accessibility</span></span>|<span data-ttu-id="dc0c4-121">Accessibilité déclarée du membre autorisée</span><span class="sxs-lookup"><span data-stu-id="dc0c4-121">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="dc0c4-122">Aucune</span><span class="sxs-lookup"><span data-stu-id="dc0c4-122">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal`|  
|`interface`|`public`|<span data-ttu-id="dc0c4-123">Aucune</span><span class="sxs-lookup"><span data-stu-id="dc0c4-123">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="dc0c4-124">L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-124">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="dc0c4-125">Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="dc0c4-125">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc0c4-126">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dc0c4-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc0c4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc0c4-127">See Also</span></span>  
 <span data-ttu-id="dc0c4-128">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dc0c4-129">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dc0c4-130">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="dc0c4-131">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-131">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="dc0c4-132">[Domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-132">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md) </span></span>  
 <span data-ttu-id="dc0c4-133">[Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-133">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="dc0c4-134">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-134">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="dc0c4-135">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-135">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="dc0c4-136">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-136">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="dc0c4-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="dc0c4-137">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="dc0c4-138">internal</span><span class="sxs-lookup"><span data-stu-id="dc0c4-138">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

