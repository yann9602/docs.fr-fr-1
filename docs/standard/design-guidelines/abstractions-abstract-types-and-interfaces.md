---
title: Abstractions (Types et interfaces abstraits)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="d40f1-102">Abstractions (Types et interfaces abstraits)</span><span class="sxs-lookup"><span data-stu-id="d40f1-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="d40f1-103">Une abstraction est un type qui décrit un contrat, mais ne fournit pas une implémentation complète du contrat.</span><span class="sxs-lookup"><span data-stu-id="d40f1-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="d40f1-104">Abstractions sont généralement implémentées en tant que classes abstraites ou interfaces, et ils sont livrés avec un ensemble bien défini de la documentation de référence décrivant les sémantiques requises des types qui implémente le contrat.</span><span class="sxs-lookup"><span data-stu-id="d40f1-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="d40f1-105">Voici quelques-uns des abstractions plus importantes dans le .NET Framework <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, et <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d40f1-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="d40f1-106">Vous pouvez étendre des infrastructures en implémentant un type concret qui prend en charge le contrat d’une abstraction et de l’utilisation de ce type concret avec framework API consommation (exploitation de) l’abstraction.</span><span class="sxs-lookup"><span data-stu-id="d40f1-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="d40f1-107">Une abstraction pertinentes et utile qui est capable de supporter le test de temps est très difficile de concevoir.</span><span class="sxs-lookup"><span data-stu-id="d40f1-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="d40f1-108">La principale difficulté consiste à obtenir l’ensemble approprié de membres, pas plus et moins non.</span><span class="sxs-lookup"><span data-stu-id="d40f1-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="d40f1-109">Si une abstraction comporte trop de membres, il devient difficile, voire même d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="d40f1-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="d40f1-110">S’il a trop peu de membres pour la fonctionnalité Promise, elle devient inutile dans de nombreux scénarios intéressants.</span><span class="sxs-lookup"><span data-stu-id="d40f1-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="d40f1-111">Les abstractions trop nombreux dans une infrastructure affectent également négatif facilité d’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="d40f1-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="d40f1-112">Il est souvent très difficile à comprendre une abstraction sans avoir à comprendre comment elle s’adapte à l’image supérieure des implémentations concrètes et les API d’exploitation sur l’abstraction.</span><span class="sxs-lookup"><span data-stu-id="d40f1-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="d40f1-113">En outre, les noms des abstractions et leurs membres sont nécessairement abstraites, qui les rend difficiles à déchiffrer et difficiles à réaliser sans premier comprendre le contexte plus large de leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="d40f1-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="d40f1-114">Toutefois, les abstractions fournissent extrêmement puissante d’extensibilité que les autres mécanismes d’extensibilité ne peuvent pas correspondre souvent.</span><span class="sxs-lookup"><span data-stu-id="d40f1-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="d40f1-115">Elles sont au cœur de nombreux modèles d’architecture, tels que les plug-ins, inversion de contrôle (IoC), pipelines et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d40f1-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="d40f1-116">Ils sont également extrêmement importants pour la testabilité des infrastructures.</span><span class="sxs-lookup"><span data-stu-id="d40f1-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="d40f1-117">Abstractions bon rendent possible d’extraire des dépendances importantes à des fins de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="d40f1-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="d40f1-118">En résumé, les abstractions sont responsables de la richesse précieuses des infrastructures et orienté objet modernes.</span><span class="sxs-lookup"><span data-stu-id="d40f1-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="d40f1-119">**X ne sont pas** fournissent des abstractions, sauf si elles sont testées par le développement de plusieurs implémentations concrètes et consomme les abstractions des API.</span><span class="sxs-lookup"><span data-stu-id="d40f1-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="d40f1-120">**✓ FAIRE** choisir entre une classe abstraite et une interface avec soin lors de la conception d’une abstraction.</span><span class="sxs-lookup"><span data-stu-id="d40f1-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="d40f1-121">**✓ Envisagez** fournissant des tests de référence pour les implémentations concrètes d’abstractions.</span><span class="sxs-lookup"><span data-stu-id="d40f1-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="d40f1-122">Ces tests doivent permettre aux utilisateurs de vérifier si leurs implémentations implémentent correctement le contrat.</span><span class="sxs-lookup"><span data-stu-id="d40f1-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="d40f1-123">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="d40f1-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d40f1-124">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d40f1-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40f1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d40f1-125">See Also</span></span>  
 [<span data-ttu-id="d40f1-126">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d40f1-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="d40f1-127">Conception en vue de l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="d40f1-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
