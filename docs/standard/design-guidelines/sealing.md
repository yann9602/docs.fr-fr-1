---
title: Sceller
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8caa253a3f17c58f542317de579c4f7832c4efac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sealing"></a><span data-ttu-id="8eaa3-102">Sceller</span><span class="sxs-lookup"><span data-stu-id="8eaa3-102">Sealing</span></span>
<span data-ttu-id="8eaa3-103">Une des fonctionnalités des infrastructures d’orientée objet est que les développeurs peuvent étendre et personnalisez-les de manières inattendues par les concepteurs de framework.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="8eaa3-104">Il s’agit la puissance et le risque de conception extensible.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="8eaa3-105">Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement pour l’extensibilité lorsqu’il est nécessaire et pour limiter l’extensibilité lorsqu’il est dangereux.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="8eaa3-106">Scellement d’un mécanisme puissant qui empêche d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="8eaa3-107">Vous pouvez sceller à la classe ou des membres individuels.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="8eaa3-108">Le fait de sceller une classe d’empêche les utilisateurs d’hériter de la classe.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="8eaa3-109">Le fait de sceller un membre d’empêche les utilisateurs de substituer un membre particulier.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="8eaa3-110">**X ne sont pas** sceller des classes sans avoir une bonne raison de le faire.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="8eaa3-111">Le fait de sceller une classe, car vous ne savez pas un scénario d’extensibilité n’est pas une bonne raison.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="8eaa3-112">Les utilisateurs de Framework tels que d’hériter des classes pour différentes raisons identifiable, telles que l’ajout de membres de commodité.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="8eaa3-113">Consultez [Classes Unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md) pour obtenir des exemples de raisons identifiable les utilisateurs souhaitent hériter d’un type.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="8eaa3-114">Raisons pour sceller une classe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8eaa3-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="8eaa3-115">La classe est une classe statique.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-115">The class is a static class.</span></span> <span data-ttu-id="8eaa3-116">Consultez [conception d’une classe statique](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="8eaa3-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="8eaa3-117">La classe stocke des secrets de sécurité sensibles dans des membres protégés hérités.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="8eaa3-118">La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement serait dépassent les avantages de la classe non scellés.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="8eaa3-119">La classe est un attribut qui nécessite la recherche d’exécution très rapide.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="8eaa3-120">Les attributs sealed ont des niveaux de performance légèrement plus élevées que celles non scellés.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="8eaa3-121">consultez [attributs](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8eaa3-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="8eaa3-122">**X ne sont pas** déclarer les membres virtuels ou protégés sur les types sealed.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="8eaa3-123">Par définition, les types sealed ne peut pas être héritées.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="8eaa3-124">Cela signifie que les membres protégés sur les types sealed ne peut pas être appelées, et les méthodes virtuelles sur les types sealed ne peut pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="8eaa3-125">**✓ Envisagez** sceller les membres que vous substituez.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="8eaa3-126">Des problèmes qui peuvent résulter de présentation des membres virtuels (présentés dans [membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)) s’appliquent aux substitutions, bien qu’à un degré moindre.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="8eaa3-127">Le fait de sceller un remplacement vous protège ces problèmes, en commençant à partir de ce point dans la hiérarchie d’héritage.</span><span class="sxs-lookup"><span data-stu-id="8eaa3-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="8eaa3-128">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="8eaa3-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8eaa3-129">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="8eaa3-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eaa3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8eaa3-130">See Also</span></span>  
 [<span data-ttu-id="8eaa3-131">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8eaa3-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="8eaa3-132">Conception d’extensibilité</span><span class="sxs-lookup"><span data-stu-id="8eaa3-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="8eaa3-133">Classes unsealed</span><span class="sxs-lookup"><span data-stu-id="8eaa3-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
