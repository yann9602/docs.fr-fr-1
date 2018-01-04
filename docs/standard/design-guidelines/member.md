---
title: Instructions de conception des membres
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae69b77098c7f2e1de83eedd40cf0f0da9473326
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="member-design-guidelines"></a><span data-ttu-id="86c3b-102">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="86c3b-102">Member Design Guidelines</span></span>
<span data-ttu-id="86c3b-103">Méthodes, propriétés, événements, constructeurs et les champs sont collectivement en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="86c3b-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="86c3b-104">Les membres sont finalement les moyens par lesquels les fonctionnalités de framework sont exposées aux utilisateurs finaux d’une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="86c3b-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="86c3b-105">Les membres peuvent être virtuel ou non virtuelle, concret ou abstrait, statique ou instance et peuvent avoir plusieurs étendues différentes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="86c3b-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="86c3b-106">Tous les différents fournit incroyable simplicité, mais en même temps requiert soins par le Concepteur de framework.</span><span class="sxs-lookup"><span data-stu-id="86c3b-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="86c3b-107">Ce chapitre propose des conseils de base qui doivent être suivies lors de la conception des membres de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="86c3b-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86c3b-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="86c3b-108">In This Section</span></span>  
 [<span data-ttu-id="86c3b-109">Surcharge de membre</span><span class="sxs-lookup"><span data-stu-id="86c3b-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="86c3b-110">Conception des propriétés</span><span class="sxs-lookup"><span data-stu-id="86c3b-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="86c3b-111">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="86c3b-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="86c3b-112">Conception d’événements</span><span class="sxs-lookup"><span data-stu-id="86c3b-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="86c3b-113">Conception de champs</span><span class="sxs-lookup"><span data-stu-id="86c3b-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="86c3b-114">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="86c3b-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="86c3b-115">Surcharges d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="86c3b-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="86c3b-116">Conception de paramètres</span><span class="sxs-lookup"><span data-stu-id="86c3b-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="86c3b-117">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="86c3b-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="86c3b-118">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="86c3b-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c3b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86c3b-119">See Also</span></span>  
 [<span data-ttu-id="86c3b-120">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="86c3b-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
