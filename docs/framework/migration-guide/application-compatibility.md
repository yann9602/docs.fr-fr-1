---
title: "Compatibilité des applications dans le .NET Framework"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e67fff19c4b187010b35519081f46e11effbad6c
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2017
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="1846b-102">Compatibilité des applications dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1846b-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="1846b-103">Introduction</span><span class="sxs-lookup"><span data-stu-id="1846b-103">Introduction</span></span>
<span data-ttu-id="1846b-104">La compatibilité est un objectif très important de chaque version de .NET.</span><span class="sxs-lookup"><span data-stu-id="1846b-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="1846b-105">La compatibilité garantit que chaque version est additive et que les versions précédentes fonctionnent donc toujours.</span><span class="sxs-lookup"><span data-stu-id="1846b-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="1846b-106">En revanche, les modifications apportées aux fonctionnalités précédentes (pour améliorer les performances, résoudre des problèmes de sécurité ou corriger des bogues) peuvent provoquer des problèmes de compatibilité dans le code ou des applications qui s’exécutent sous une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1846b-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="1846b-107">Le .NET Framework reconnaît les modifications de reciblage et du runtime.</span><span class="sxs-lookup"><span data-stu-id="1846b-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="1846b-108">Les modifications de reciblage concernent les applications qui ciblent une version spécifique du .NET Framework, mais sont exécutées sur une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1846b-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="1846b-109">Les modifications du runtime concernent toutes les applications qui s’exécutent sur une version particulière.</span><span class="sxs-lookup"><span data-stu-id="1846b-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="1846b-110">Chaque application cible une version spécifique du .NET Framework, qui peut être indiquée par :</span><span class="sxs-lookup"><span data-stu-id="1846b-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="1846b-111">La définition d’une version cible de .NET Framework dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1846b-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="1846b-112">La spécification de la version cible de .NET Framework dans un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="1846b-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="1846b-113">L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.</span><span class="sxs-lookup"><span data-stu-id="1846b-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="1846b-114">Lors de l’exécution sur une version plus récente que celle qui était ciblée, le .NET Framework utilise un subterfuge afin de simuler l’ancienne version ciblée.</span><span class="sxs-lookup"><span data-stu-id="1846b-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="1846b-115">En d’autres termes, l’application s’exécute sur la version la plus récente du .NET Framework, mais agit comme si elle était exécutée sur la version antérieure.</span><span class="sxs-lookup"><span data-stu-id="1846b-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="1846b-116">La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge.</span><span class="sxs-lookup"><span data-stu-id="1846b-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="1846b-117">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="1846b-117">Runtime changes</span></span>

<span data-ttu-id="1846b-118">Les problèmes de runtime sont ceux qui surviennent quand un nouveau runtime est placé sur un ordinateur, que les mêmes fichiers binaires sont exécutés, mais qu’un comportement différent est détecté.</span><span class="sxs-lookup"><span data-stu-id="1846b-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="1846b-119">Si un fichier binaire a été compilé pour .NET Framework 4.0, il est exécuté en mode de compatibilité .NET Framework 4.0 sur les versions 4.5 ou ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1846b-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="1846b-120">La plupart des modifications qui affectent 4.5 n’affectent pas un fichier binaire compilé pour la version 4.0.</span><span class="sxs-lookup"><span data-stu-id="1846b-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="1846b-121">Cela est spécifique au domaine d’application et dépend des paramètres de l’assembly d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1846b-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="1846b-122">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="1846b-122">Retargeting changes</span></span>

<span data-ttu-id="1846b-123">Les problèmes de reciblage sont ceux qui surviennent quand un assembly qui ciblait 4.0 est maintenant défini pour cibler 4.5.</span><span class="sxs-lookup"><span data-stu-id="1846b-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="1846b-124">Maintenant, l’assembly accepte les nouvelles fonctionnalités ainsi que les éventuels problèmes de compatibilité des anciennes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="1846b-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="1846b-125">Là encore, cela dépend de l’assembly d’entrée, comme l’application console qui utilise l’assembly ou le site web qui fait référence à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1846b-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="1846b-126">Diagnostics de compatibilité .NET</span><span class="sxs-lookup"><span data-stu-id="1846b-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="1846b-127">Les diagnostics de compatibilité .NET sont des analyseurs issus de la technologie Roslyn qui permettent d’identifier les problèmes de compatibilité entre les différentes versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1846b-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="1846b-128">Cette liste contient tous les analyseurs disponibles, même si chaque migration ne nécessite qu’une partie de ces analyseurs.</span><span class="sxs-lookup"><span data-stu-id="1846b-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="1846b-129">Les analyseurs permettent de déterminer les problèmes liés à la migration planifiée et signalent uniquement ce type de problèmes.</span><span class="sxs-lookup"><span data-stu-id="1846b-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="1846b-130">Chaque problème comprend les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1846b-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="1846b-131">La description de ce qui a changé par rapport à la version précédente.</span><span class="sxs-lookup"><span data-stu-id="1846b-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="1846b-132">La façon dont ce changement affecte les clients et si d’éventuelles solutions de contournement sont disponibles pour préserver la compatibilité entre les versions.</span><span class="sxs-lookup"><span data-stu-id="1846b-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="1846b-133">Une évaluation de l’importance du changement.</span><span class="sxs-lookup"><span data-stu-id="1846b-133">An assessment of how important the change is.</span></span> <span data-ttu-id="1846b-134">Les problèmes de compatibilité entre applications sont classés de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="1846b-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="1846b-135">Majeur</span><span class="sxs-lookup"><span data-stu-id="1846b-135">Major</span></span>|<span data-ttu-id="1846b-136">Modification importante qui affecte un grand nombre d’applications ou qui nécessite de modifier significativement le code.</span><span class="sxs-lookup"><span data-stu-id="1846b-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="1846b-137">Mineur</span><span class="sxs-lookup"><span data-stu-id="1846b-137">Minor</span></span>|<span data-ttu-id="1846b-138">Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.</span><span class="sxs-lookup"><span data-stu-id="1846b-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="1846b-139">Cas limite</span><span class="sxs-lookup"><span data-stu-id="1846b-139">Edge case</span></span>|<span data-ttu-id="1846b-140">Modification qui affecte des applications dans des scénarios très spécifiques et peu courants.</span><span class="sxs-lookup"><span data-stu-id="1846b-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="1846b-141">Transparent</span><span class="sxs-lookup"><span data-stu-id="1846b-141">Transparent</span></span>|<span data-ttu-id="1846b-142">Modification qui n’a pas d’effet visible pour le développeur ou l’utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="1846b-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="1846b-143">La version indique à quel moment cette modification est apparue pour la première fois dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1846b-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="1846b-144">Certaines modifications sont introduites dans une version particulière et annulées dans une version ultérieure ; cela est également indiqué.</span><span class="sxs-lookup"><span data-stu-id="1846b-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="1846b-145">Type de modification :</span><span class="sxs-lookup"><span data-stu-id="1846b-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="1846b-146">Reciblage</span><span class="sxs-lookup"><span data-stu-id="1846b-146">Retargeting</span></span>|<span data-ttu-id="1846b-147">La modification affecte les applications qui sont recompilées pour cibler une nouvelle version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1846b-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="1846b-148">Exécution</span><span class="sxs-lookup"><span data-stu-id="1846b-148">Runtime</span></span>|<span data-ttu-id="1846b-149">La modification affecte une application existante qui cible une version antérieure du .NET Framework, mais s’exécute sur une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1846b-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="1846b-150">Les API affectées, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="1846b-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="1846b-151">Les ID des diagnostics disponibles</span><span class="sxs-lookup"><span data-stu-id="1846b-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="1846b-152">Utilisation</span><span class="sxs-lookup"><span data-stu-id="1846b-152">Usage</span></span>
<span data-ttu-id="1846b-153">Pour commencer, sélectionnez le type de modification de la compatibilité ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1846b-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="1846b-154">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="1846b-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="1846b-155">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="1846b-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="1846b-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1846b-156">See Also</span></span>

* [<span data-ttu-id="1846b-157">Versions et dépendances</span><span class="sxs-lookup"><span data-stu-id="1846b-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="1846b-158">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="1846b-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="1846b-159">Éléments obsolètes dans la bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="1846b-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
