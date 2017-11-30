---
title: Membres virtuels
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56838fc4c1c1e7cb8723beee3f0e6b23515d43f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-members"></a><span data-ttu-id="b109f-102">Membres virtuels</span><span class="sxs-lookup"><span data-stu-id="b109f-102">Virtual Members</span></span>
<span data-ttu-id="b109f-103">Membres virtuels peuvent être substituées, ce qui modifie le comportement de la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="b109f-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="b109f-104">Elles sont très similaires aux rappels en termes de l’extensibilité, qu'ils fournissent, mais ils sont mieux en termes de performances de l’exécution et la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b109f-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="b109f-105">En outre, les membres virtuels se sentent plus naturels dans les scénarios qui requièrent la création d’un spécial type d’un type existant (spécialisation).</span><span class="sxs-lookup"><span data-stu-id="b109f-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="b109f-106">Membres virtuels plus performants que les rappels et les événements, mais n’effectuent pas de meilleures performances que les méthodes non virtuelles.</span><span class="sxs-lookup"><span data-stu-id="b109f-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="b109f-107">Le principal inconvénient des membres virtuels est que le comportement d’un membre virtuel peut uniquement être modifié au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b109f-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="b109f-108">Le comportement d’un rappel peut être modifié lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b109f-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="b109f-109">Les membres virtuels, comme des rappels (et peut-être plusieurs rappels), sont coûteuses à concevoir, tester et mettre à jour, car un appel à un membre virtuel peut être substitué de manière imprévisible et peut exécuter du code arbitraire.</span><span class="sxs-lookup"><span data-stu-id="b109f-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="b109f-110">En outre, beaucoup plus d’effort est généralement requis pour définir clairement le contrat de membres virtuels, ce qui augmente le coût de la conception et à les documenter.</span><span class="sxs-lookup"><span data-stu-id="b109f-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="b109f-111">**X ne sont pas** rendre les membres virtuels sauf si vous avez une bonne raison à cela et que vous connaissez tous les coûts liés à la conception, de test et de maintenance des membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="b109f-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="b109f-112">Membres virtuels sont moins indulgent en termes de modifications qui peuvent être mises sans rompre la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="b109f-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="b109f-113">En outre, ils sont plus lentes que les membres non virtuelle, principalement parce que les appels aux membres virtuels ne sont pas inline.</span><span class="sxs-lookup"><span data-stu-id="b109f-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="b109f-114">**✓ Envisagez** limiter l’extensibilité à celles qui sont absolument nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b109f-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="b109f-115">**✓ FAIRE** accessibilité protégée préférer une accessibilité publique pour les membres virtuels.</span><span class="sxs-lookup"><span data-stu-id="b109f-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="b109f-116">Les membres publics doivent fournir l’extensibilité (si nécessaire) en appelant un membre virtuel protégé.</span><span class="sxs-lookup"><span data-stu-id="b109f-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="b109f-117">Les membres publics d’une classe doivent fournir l’ensemble approprié de fonctionnalités pour les consommateurs directs de cette classe.</span><span class="sxs-lookup"><span data-stu-id="b109f-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="b109f-118">Membres virtuels sont conçus pour être substitué dans les sous-classes et accessibilité protégée est un excellent moyen de l’étendue de tous les points d’extensibilité virtuel où elles peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="b109f-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="b109f-119">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="b109f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b109f-120">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b109f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b109f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b109f-121">See Also</span></span>  
 [<span data-ttu-id="b109f-122">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b109f-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b109f-123">Conception d’extensibilité</span><span class="sxs-lookup"><span data-stu-id="b109f-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
