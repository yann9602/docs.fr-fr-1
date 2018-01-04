---
title: Instructions de conception de types
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6b02abef0180b6de82e26837863849cce35c994f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="type-design-guidelines"></a><span data-ttu-id="d8eb7-102">Instructions de conception de types</span><span class="sxs-lookup"><span data-stu-id="d8eb7-102">Type Design Guidelines</span></span>
<span data-ttu-id="d8eb7-103">Du point de vue du CLR, il existe uniquement deux catégories de types : types référence et les types valeur, mais pour une discussion sur la conception d’infrastructure, nous allons diviser les types en groupes plus logiques, chacun avec ses propres règles de conception spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="d8eb7-104">Les classes sont des types de référence de manière générale.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="d8eb7-105">Ils constituent la majorité des types dans la plupart des infrastructures.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="d8eb7-106">Classes à régler leur fréquence pour la riche ensemble de fonctionnalités orientées objet qu’ils prennent en charge et leur applicabilité générale.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="d8eb7-107">Classes de base et les classes abstraites sont des groupes logiques spéciales relatives à l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="d8eb7-108">Les interfaces sont des types qui peuvent être implémentées par les types référence et les types de valeur.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="d8eb7-109">Elles constituent donc racines des hiérarchies polymorphes des types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="d8eb7-110">En outre, interfaces peuvent être utilisés pour simuler l’héritage multiple, ce qui n’est pas pris en charge en mode natif par le CLR.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="d8eb7-111">Les structures sont des types de valeur de manière générale et doivent être réservés pour les types simples, comme des primitives de langage.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="d8eb7-112">Les énumérations sont un cas spécial de types valeur utilisés pour définir des jeux court de valeurs, telles que des jours de la semaine, les couleurs de console et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="d8eb7-113">Les classes statiques sont destinés à être des conteneurs pour les membres statiques de types.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="d8eb7-114">Elles sont utilisées pour fournir des raccourcis vers les autres opérations.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="d8eb7-115">Les délégués, des exceptions, des attributs, des tableaux et des collections sont tous les cas spéciaux de types de référence prévus pour des utilisations spécifiques, et des recommandations pour la conception et d’utilisation sont traitées ailleurs dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="d8eb7-116">**✓ FAIRE** Vérifiez que chaque type est un ensemble bien défini de membres associés, pas seulement une collection aléatoire des fonctionnalités non liées.</span><span class="sxs-lookup"><span data-stu-id="d8eb7-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8eb7-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d8eb7-117">In This Section</span></span>  
 [<span data-ttu-id="d8eb7-118">Choix entre classe et structure</span><span class="sxs-lookup"><span data-stu-id="d8eb7-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="d8eb7-119">Conception de classes abstraites</span><span class="sxs-lookup"><span data-stu-id="d8eb7-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="d8eb7-120">Conception de classes statiques</span><span class="sxs-lookup"><span data-stu-id="d8eb7-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="d8eb7-121">Conception d’interfaces</span><span class="sxs-lookup"><span data-stu-id="d8eb7-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="d8eb7-122">Conception de structures</span><span class="sxs-lookup"><span data-stu-id="d8eb7-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="d8eb7-123">Conception d’énumérations</span><span class="sxs-lookup"><span data-stu-id="d8eb7-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="d8eb7-124">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="d8eb7-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="d8eb7-125">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="d8eb7-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d8eb7-126">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d8eb7-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8eb7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8eb7-127">See Also</span></span>  
 [<span data-ttu-id="d8eb7-128">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8eb7-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
