---
title: "Types imbriqués"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 389ba73c4509f41f6c2cf86363e59ea720eb3c9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="nested-types"></a><span data-ttu-id="d984d-102">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="d984d-102">Nested Types</span></span>
<span data-ttu-id="d984d-103">Un type imbriqué est un type défini dans l’étendue d’un autre type, qui est appelé le type englobant.</span><span class="sxs-lookup"><span data-stu-id="d984d-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="d984d-104">Un type imbriqué a accès à tous les membres de son type englobant.</span><span class="sxs-lookup"><span data-stu-id="d984d-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="d984d-105">Par exemple, il a accès à des champs privés définis dans le type englobant et protéger les champs définis dans tous les ascendants du type englobant.</span><span class="sxs-lookup"><span data-stu-id="d984d-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="d984d-106">En général, les types imbriqués doivent être utilisés avec modération.</span><span class="sxs-lookup"><span data-stu-id="d984d-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="d984d-107">et ce, pour plusieurs raisons.</span><span class="sxs-lookup"><span data-stu-id="d984d-107">There are several reasons for this.</span></span> <span data-ttu-id="d984d-108">Certains développeurs ne connaissent pas complètement le concept.</span><span class="sxs-lookup"><span data-stu-id="d984d-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="d984d-109">Les développeurs peuvent, par exemple, rencontrer des problèmes avec la syntaxe de déclaration de variables de types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d984d-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="d984d-110">Les types imbriqués sont également très étroitement avec leurs types englobants et par conséquent ne sont pas adaptés pour être des types à usage général.</span><span class="sxs-lookup"><span data-stu-id="d984d-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="d984d-111">Les types imbriqués sont mieux adaptées pour modéliser les détails d’implémentation de ses types englobants.</span><span class="sxs-lookup"><span data-stu-id="d984d-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="d984d-112">L’utilisateur final doivent rarement avoir à déclarer des variables d’un type imbriqué et presque jamais devez instancier explicitement les types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d984d-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="d984d-113">Par exemple, l’énumérateur d’une collection peut être un type imbriqué de cette collection.</span><span class="sxs-lookup"><span data-stu-id="d984d-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="d984d-114">En général, les énumérateurs sont instanciés par leur type englobant, et de nombreux langages prenant en charge l’instruction foreach, les variables de l’énumérateur ont rarement être déclaré par l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="d984d-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="d984d-115">**✓ FAIRE** utilisez des types imbriqués lorsque la relation entre le type imbriqué et son type externe est telle que sémantique de l’accessibilité des membres est souhaitable.</span><span class="sxs-lookup"><span data-stu-id="d984d-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="d984d-116">**X ne sont pas** utiliser les types imbriqués publics en tant qu’un regroupement logique construire ; utilisez des espaces de noms pour ce.</span><span class="sxs-lookup"><span data-stu-id="d984d-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="d984d-117">**X Évitez** exposées publiquement des types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d984d-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="d984d-118">La seule exception est si les variables du type imbriqué doivent être déclarées que dans les rares scénarios sous-classement ou d’autres scénarios de personnalisation avancées.</span><span class="sxs-lookup"><span data-stu-id="d984d-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="d984d-119">**X ne sont pas** utilisez des types imbriqués, si le type est susceptible d’être référencés en dehors du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="d984d-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="d984d-120">Par exemple, un enum passé à une méthode définie sur une classe ne doit pas être défini comme un type imbriqué dans la classe.</span><span class="sxs-lookup"><span data-stu-id="d984d-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="d984d-121">**X ne sont pas** utilisez des types imbriqués s’ils doivent être instancié par le code client.</span><span class="sxs-lookup"><span data-stu-id="d984d-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="d984d-122">Si un type a un constructeur public, il doit probablement pas être imbriqué.</span><span class="sxs-lookup"><span data-stu-id="d984d-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="d984d-123">Si un type peut être instancié, qui semble indiquer le type a un lieu dans le cadre de son propre (vous pouvez créer, utiliser et détruire sans passer par le type externe) et ne doivent donc pas être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="d984d-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="d984d-124">Types internes ne doivent pas être réutilisés largement en dehors du type externe sans aucune relation quelque type externe.</span><span class="sxs-lookup"><span data-stu-id="d984d-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="d984d-125">**X ne sont pas** définir un type imbriqué en tant que membre d’une interface.</span><span class="sxs-lookup"><span data-stu-id="d984d-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="d984d-126">De nombreux langages ne gèrent pas une construction de ce type.</span><span class="sxs-lookup"><span data-stu-id="d984d-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="d984d-127">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="d984d-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d984d-128">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d984d-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d984d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d984d-129">See Also</span></span>  
 [<span data-ttu-id="d984d-130">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="d984d-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="d984d-131">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d984d-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
