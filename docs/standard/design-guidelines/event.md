---
title: "Conception d'événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8dcd1003b3f93db733ece4f90340d1d98867d2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="event-design"></a><span data-ttu-id="6a979-102">Conception d'événements</span><span class="sxs-lookup"><span data-stu-id="6a979-102">Event Design</span></span>
<span data-ttu-id="6a979-103">Les événements sont la forme couramment utilisée de rappels (les constructions qui autorisent l’infrastructure pour appeler dans du code de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="6a979-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="6a979-104">Autres mécanismes de rappel incluent les membres avec les délégués, les membres virtuels et basée sur l’interface de plug-ins. Les données à partir des études de convivialité indiquent que la majorité des développeurs sont plus à l’aise avec les événements qu’ils utilisent d’autres méthodes de rappel.</span><span class="sxs-lookup"><span data-stu-id="6a979-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="6a979-105">Les événements sont bien intégrés à Visual Studio et de nombreux langages.</span><span class="sxs-lookup"><span data-stu-id="6a979-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="6a979-106">Il est important de noter qu’il n’y a deux groupes d’événements : événements déclenchés avant un état des modifications système, appelé pré-événements et les événements déclenchés après le change d’un état, appelée post événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="6a979-107">Un exemple d’un événement avant serait `Form.Closing`, qui est déclenché avant la fermeture d’un formulaire.</span><span class="sxs-lookup"><span data-stu-id="6a979-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="6a979-108">Un exemple d’un post-événement `Form.Closed`, qui est déclenché lorsqu’un formulaire est fermé.</span><span class="sxs-lookup"><span data-stu-id="6a979-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="6a979-109">**✓ FAIRE** utiliser le terme « r » pour les événements plutôt que « fire » ou « déclenche ».</span><span class="sxs-lookup"><span data-stu-id="6a979-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="6a979-110">**✓ FAIRE** utiliser <xref:System.EventHandler%601?displayProperty=nameWithType> au lieu de créer manuellement les nouveaux délégués à utiliser en tant que gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="6a979-111">**ENVISAGEZ de ✓** à l’aide d’une sous-classe de <xref:System.EventArgs> comme argument d’événement, sauf si vous êtes absolument que l’événement n’est jamais nécessaire de transporter des données à l’événement de gestion de la méthode, auquel cas vous pouvez utiliser la `EventArgs` taper directement.</span><span class="sxs-lookup"><span data-stu-id="6a979-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="6a979-112">Si vous livrez une à l’aide de l’API `EventArgs` directement, vous ne pourrez jamais ajouter des données à effectuer sans rompre la compatibilité avec l’événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="6a979-113">Si vous utilisez une sous-classe, même si initialement vide, vous serez en mesure d’ajouter des propriétés à la sous-classe si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6a979-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="6a979-114">**✓ FAIRE** utiliser une méthode virtuelle protégée pour déclencher chaque événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="6a979-115">Cela s’applique uniquement aux événements non statiques sur les classes non scellés, pas pour les structures, les classes sealed ou aux événements statiques.</span><span class="sxs-lookup"><span data-stu-id="6a979-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="6a979-116">L’objectif de la méthode est d’offrir un moyen d’une classe dérivée gérer l’événement à l’aide d’un remplacement.</span><span class="sxs-lookup"><span data-stu-id="6a979-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="6a979-117">La substitution est un moyen plus naturel, plus rapide et plus souple pour gérer les événements de la classe de base dans les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="6a979-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="6a979-118">Par convention, le nom de la méthode doit commencer par « On » et être suivi par le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="6a979-119">La classe dérivée peut choisissez de ne pas appeler l’implémentation de la méthode de base dans son remplacement.</span><span class="sxs-lookup"><span data-stu-id="6a979-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="6a979-120">Attendez-vous à cela en n’incluant aucun traitement dans la méthode qui est requise pour la classe de base fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="6a979-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="6a979-121">**✓ FAIRE** doit accepter un paramètre à la méthode protégée qui déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="6a979-122">Le paramètre doit être nommé `e` et doit être tapé sous forme de la classe d’argument d’événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="6a979-123">**X ne sont pas** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement non statique.</span><span class="sxs-lookup"><span data-stu-id="6a979-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="6a979-124">**✓ FAIRE** passez la valeur null en tant que l’expéditeur lors du déclenchement d’un événement statique.</span><span class="sxs-lookup"><span data-stu-id="6a979-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="6a979-125">**X ne sont pas** passez la valeur null en tant que le paramètre de données d’événement lors du déclenchement d’un événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="6a979-126">Vous devez passer `EventArgs.Empty` si vous ne souhaitez pas passer des données à la méthode de gestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="6a979-127">Les développeurs s’attendent à ce paramètre ne pas pour avoir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="6a979-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="6a979-128">**✓ Envisagez** le déclenchement d’événements de l’utilisateur final peut annuler.</span><span class="sxs-lookup"><span data-stu-id="6a979-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="6a979-129">Cela s’applique uniquement aux événements antérieurs.</span><span class="sxs-lookup"><span data-stu-id="6a979-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="6a979-130">Utilisez <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ou sa sous-classe comme argument d’événement pour autoriser l’utilisateur final d’annuler des événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="6a979-131">Conception de gestionnaires d’événements personnalisés</span><span class="sxs-lookup"><span data-stu-id="6a979-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="6a979-132">Il existe des cas dans lequel `EventHandler<T>` ne peut pas être utilisé, tel que lorsque l’infrastructure a besoin travailler avec les versions antérieures du CLR, ce qui ne prend pas en charge les génériques.</span><span class="sxs-lookup"><span data-stu-id="6a979-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="6a979-133">Dans ce cas, vous devrez peut-être concevoir et développer un délégué de gestionnaire d’événements personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6a979-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="6a979-134">**✓ FAIRE** utiliser un type de retour void pour les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="6a979-135">Un gestionnaire d’événements peut appeler plusieurs méthodes, éventuellement sur plusieurs objets de gestion d’événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="6a979-136">Si les méthodes de gestion des événements ont été autorisées pour retourner une valeur, il y aura plusieurs valeurs de retour pour chaque appel de l’événement.</span><span class="sxs-lookup"><span data-stu-id="6a979-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="6a979-137">**✓ FAIRE** utiliser `object` en tant que le type du premier paramètre du Gestionnaire d’événements et l’appeler `sender`.</span><span class="sxs-lookup"><span data-stu-id="6a979-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="6a979-138">**✓ FAIRE** utiliser <xref:System.EventArgs?displayProperty=nameWithType> ou sa sous-classe en tant que le type du deuxième paramètre du Gestionnaire d’événements et l’appeler `e`.</span><span class="sxs-lookup"><span data-stu-id="6a979-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="6a979-139">**X ne sont pas** avoir plus de deux paramètres sur les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="6a979-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="6a979-140">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="6a979-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a979-141">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a979-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a979-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a979-142">See Also</span></span>  
 [<span data-ttu-id="6a979-143">Règles de conception de membres</span><span class="sxs-lookup"><span data-stu-id="6a979-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="6a979-144">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a979-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
