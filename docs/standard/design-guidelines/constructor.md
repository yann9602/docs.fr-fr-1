---
title: Conception de constructeurs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66a297ed035f5afde06913b89f1f92dee5745f48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="constructor-design"></a><span data-ttu-id="e4162-102">Conception de constructeurs</span><span class="sxs-lookup"><span data-stu-id="e4162-102">Constructor Design</span></span>
<span data-ttu-id="e4162-103">Il existe deux types de constructeurs : constructeurs et les constructeurs d’instance de type.</span><span class="sxs-lookup"><span data-stu-id="e4162-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="e4162-104">Constructeurs de type sont statiques et sont exécutées par le CLR, avant que le type est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e4162-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="e4162-105">Constructeurs d’instance exécuté lorsqu’une instance d’un type est créée.</span><span class="sxs-lookup"><span data-stu-id="e4162-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="e4162-106">Constructeurs de type ne peut pas prendre des paramètres.</span><span class="sxs-lookup"><span data-stu-id="e4162-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="e4162-107">Constructeurs d’instance peuvent.</span><span class="sxs-lookup"><span data-stu-id="e4162-107">Instance constructors can.</span></span> <span data-ttu-id="e4162-108">Constructeurs d’instance qui n’acceptent aucun paramètre sont souvent appelés des constructeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4162-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="e4162-109">Les constructeurs sont la façon la plus naturelle pour créer des instances d’un type.</span><span class="sxs-lookup"><span data-stu-id="e4162-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="e4162-110">La plupart des développeurs recherche et essayez d’utiliser un constructeur avant d’autres méthodes pour créer des instances (par exemple, les méthodes de fabrique).</span><span class="sxs-lookup"><span data-stu-id="e4162-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="e4162-111">**✓ Envisagez** fournissant simple, dans l’idéal, par défaut, les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="e4162-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="e4162-112">Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou enums.</span><span class="sxs-lookup"><span data-stu-id="e4162-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="e4162-113">Ces constructeurs simples faciliter l’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e4162-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="e4162-114">**✓ Envisagez** à l’aide d’une méthode de fabrique statique au lieu d’un constructeur si la sémantique de l’opération requise ne correspond pas directement à la construction d’une nouvelle instance, ou si les règles de conception du constructeur vous semblent pas naturelles.</span><span class="sxs-lookup"><span data-stu-id="e4162-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="e4162-115">**✓ FAIRE** utiliser les paramètres du constructeur en tant que raccourcis pour définir les propriétés principales.</span><span class="sxs-lookup"><span data-stu-id="e4162-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="e4162-116">Il ne doit y avoir aucune différence de sémantique entre l’utilisation du constructeur vide suivi de certains jeux de propriétés et à l’aide d’un constructeur avec plusieurs arguments.</span><span class="sxs-lookup"><span data-stu-id="e4162-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="e4162-117">**✓ FAIRE** utiliser le même nom pour les paramètres du constructeur et une propriété si les paramètres du constructeur sont utilisés pour définir simplement la propriété.</span><span class="sxs-lookup"><span data-stu-id="e4162-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="e4162-118">La seule différence entre ces paramètres et les propriétés est la casse.</span><span class="sxs-lookup"><span data-stu-id="e4162-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="e4162-119">**✓ FAIRE** travail minimal dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="e4162-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="e4162-120">Les constructeurs ne quantité de travail autre que capture les paramètres du constructeur.</span><span class="sxs-lookup"><span data-stu-id="e4162-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="e4162-121">Le coût de tout autre traitement doit être différé jusqu'à ce que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e4162-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="e4162-122">**✓ FAIRE** lever des exceptions à partir des constructeurs d’instance, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="e4162-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="e4162-123">**✓ FAIRE** déclarer explicitement le constructeur public par défaut dans les classes, si un tel constructeur est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e4162-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="e4162-124">Si vous ne déclarez explicitement de constructeur sur un type, plusieurs langues (par exemple, en c#) ajoute automatiquement un constructeur public par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4162-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="e4162-125">(Les classes abstraites obtenir un constructeur protégé.)</span><span class="sxs-lookup"><span data-stu-id="e4162-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="e4162-126">Ajout d’un constructeur paramétrable à une classe d’empêche le compilateur d’ajouter le constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e4162-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="e4162-127">Cela entraîne souvent des modifications avec rupture accidentelle.</span><span class="sxs-lookup"><span data-stu-id="e4162-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="e4162-128">**X Évitez** définition explicite des constructeurs par défaut sur les structures.</span><span class="sxs-lookup"><span data-stu-id="e4162-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="e4162-129">Cela rend la création de tableau plus rapide, car si le constructeur par défaut n’est pas défini, il n’a pas à être exécuté sur tous les emplacements dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e4162-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="e4162-130">Notez que de nombreux compilateurs, notamment c#, ne pas autoriser les structs peuvent avoir des constructeurs sans paramètre pour cette raison.</span><span class="sxs-lookup"><span data-stu-id="e4162-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="e4162-131">**X Évitez** appel des membres virtuels sur un objet à l’intérieur de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="e4162-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="e4162-132">Appel d’un membre virtuel entraînera le remplacement de la plus dérivé à appeler, même si le constructeur du type plus dérivé a été entièrement s’exécute pas encore.</span><span class="sxs-lookup"><span data-stu-id="e4162-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="e4162-133">Instructions de constructeur de type</span><span class="sxs-lookup"><span data-stu-id="e4162-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="e4162-134">**✓ FAIRE** rendre les constructeurs statiques privé.</span><span class="sxs-lookup"><span data-stu-id="e4162-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="e4162-135">Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type.</span><span class="sxs-lookup"><span data-stu-id="e4162-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="e4162-136">Le CLR appelle le constructeur statique avant la création de la première instance du type ou de tout membre statique de ce type est appelées.</span><span class="sxs-lookup"><span data-stu-id="e4162-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="e4162-137">L’utilisateur n’a aucun contrôle sur lorsque le constructeur statique est appelé.</span><span class="sxs-lookup"><span data-stu-id="e4162-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="e4162-138">Si un constructeur statique n’est pas privé, il peut être appelé par du code autre que le CLR.</span><span class="sxs-lookup"><span data-stu-id="e4162-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="e4162-139">Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="e4162-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="e4162-140">Le compilateur c# force les constructeurs statiques privé.</span><span class="sxs-lookup"><span data-stu-id="e4162-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="e4162-141">**X ne sont pas** lever des exceptions à partir des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="e4162-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="e4162-142">Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="e4162-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="e4162-143">**✓ Envisagez** initialiser les champs statiques inline au lieu d’utiliser explicitement des constructeurs statiques, car le runtime peut optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.</span><span class="sxs-lookup"><span data-stu-id="e4162-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="e4162-144">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="e4162-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e4162-145">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e4162-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4162-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4162-146">See Also</span></span>  
 [<span data-ttu-id="e4162-147">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="e4162-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="e4162-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e4162-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
