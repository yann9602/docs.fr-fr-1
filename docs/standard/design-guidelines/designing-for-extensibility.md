---
title: "Conception en vue de l'extensibilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f21e9239199ecd36432ed8f14adb896f1799506b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="366d9-102">Conception en vue de l'extensibilité</span><span class="sxs-lookup"><span data-stu-id="366d9-102">Designing for Extensibility</span></span>
<span data-ttu-id="366d9-103">Un aspect important de la conception d’une infrastructure consiste à s’assurer de que l’extensibilité de l’infrastructure a été examinée avec soin.</span><span class="sxs-lookup"><span data-stu-id="366d9-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="366d9-104">Cela nécessite que vous comprenez les coûts et les avantages associés à différents mécanismes d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="366d9-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="366d9-105">Ce chapitre vous aide à décider des mécanismes d’extensibilité : sous-classement, les événements, les membres virtuels, les rappels et ainsi de suite, peuvent mieux les exigences de votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="366d9-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="366d9-106">Il existe de nombreuses façons pour permettre d’extensibilité dans les infrastructures.</span><span class="sxs-lookup"><span data-stu-id="366d9-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="366d9-107">Elles vont de moins puissants mais moins coûteux à très puissante, mais il est coûteux.</span><span class="sxs-lookup"><span data-stu-id="366d9-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="366d9-108">Pour tous les besoins d’extensibilité donné, vous devez choisir le mécanisme d’extensibilité moins coûteux qui répond aux exigences.</span><span class="sxs-lookup"><span data-stu-id="366d9-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="366d9-109">Gardez à l’esprit qu’il est généralement possible d’ajouter plus d’extensibilité ultérieurement, mais prennent immédiatement sans introduire de modifications avec rupture jamais.</span><span class="sxs-lookup"><span data-stu-id="366d9-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="366d9-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="366d9-110">In This Section</span></span>  
 [<span data-ttu-id="366d9-111">Classes unsealed</span><span class="sxs-lookup"><span data-stu-id="366d9-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="366d9-112">Membres protégés</span><span class="sxs-lookup"><span data-stu-id="366d9-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="366d9-113">Événements et rappels</span><span class="sxs-lookup"><span data-stu-id="366d9-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="366d9-114">Membres virtuels</span><span class="sxs-lookup"><span data-stu-id="366d9-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="366d9-115">Abstractions (types et interfaces abstraits)</span><span class="sxs-lookup"><span data-stu-id="366d9-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="366d9-116">Classes de base pour l’implémentation d’abstractions</span><span class="sxs-lookup"><span data-stu-id="366d9-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="366d9-117">Scellement</span><span class="sxs-lookup"><span data-stu-id="366d9-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="366d9-118">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="366d9-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="366d9-119">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="366d9-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366d9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="366d9-120">See Also</span></span>  
 [<span data-ttu-id="366d9-121">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="366d9-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
