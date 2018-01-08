---
title: Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core
description: "Aide destinée aux propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core."
keywords: .NET, .NET Core, .NET Framework, disposition du projet, plusieurs frameworks
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.workload: dotnetcore
ms.openlocfilehash: 08fe18233c13410f0fb970020bce090d3345ca84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="435eb-104">Organisation de votre projet pour prendre en charge le .NET Framework et .NET Core</span><span class="sxs-lookup"><span data-stu-id="435eb-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="435eb-105">Cet article vise à aider les propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="435eb-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="435eb-106">Il fournit plusieurs options pour organiser les projets de façon à aider les développeurs à atteindre cet objectif.</span><span class="sxs-lookup"><span data-stu-id="435eb-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="435eb-107">La liste suivante fournit quelques scénarios classiques à prendre en compte quand vous devez décider comment configurer la disposition de votre projet avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="435eb-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="435eb-108">La liste peut ne pas couvrir tout ce que vous souhaitez : établissez vos priorités en fonction des besoins de votre projet.</span><span class="sxs-lookup"><span data-stu-id="435eb-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="435eb-109">[**Combiner des projets existants et des projets .NET Core en projets uniques**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="435eb-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="435eb-110">*En voici les avantages :*</span><span class="sxs-lookup"><span data-stu-id="435eb-110">*What this is good for:*</span></span>
  * <span data-ttu-id="435eb-111">Simplification de votre processus de génération : compilation d’un seul projet au lieu de plusieurs, chacun ciblant une version du .NET Framework ou une plateforme différente.</span><span class="sxs-lookup"><span data-stu-id="435eb-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="435eb-112">Simplification de la gestion des fichiers sources pour les projets multiciblés car vous devez gérez un seul fichier projet.</span><span class="sxs-lookup"><span data-stu-id="435eb-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="435eb-113">Lors de l’ajout/suppression de fichiers sources, les alternatives vous obligent à synchroniser manuellement ces fichiers avec vos autres projets.</span><span class="sxs-lookup"><span data-stu-id="435eb-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="435eb-114">Génération facile d’un package NuGet à consommer.</span><span class="sxs-lookup"><span data-stu-id="435eb-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="435eb-115">Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.</span><span class="sxs-lookup"><span data-stu-id="435eb-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="435eb-116">*Scénarios non pris en charge :*</span><span class="sxs-lookup"><span data-stu-id="435eb-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="435eb-117">Demander aux développeurs d’utiliser Visual Studio 2017 pour ouvrir des projets existants.</span><span class="sxs-lookup"><span data-stu-id="435eb-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="435eb-118">Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.</span><span class="sxs-lookup"><span data-stu-id="435eb-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="435eb-119">[**Séparer les projets existants des nouveaux projets .NET Core**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="435eb-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="435eb-120">*En voici les avantages :*</span><span class="sxs-lookup"><span data-stu-id="435eb-120">*What this is good for:*</span></span>
  * <span data-ttu-id="435eb-121">Continuation de la prise en charge du développement de projets existants sans devoir mettre à niveau pour les développeurs/contributeurs qui n’ont pas Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="435eb-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="435eb-122">Réduction du risque de création de bogues dans des projets existants car aucune évolution du code n’est nécessaire dans ces projets.</span><span class="sxs-lookup"><span data-stu-id="435eb-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="435eb-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="435eb-123">Example</span></span>

<span data-ttu-id="435eb-124">Considérez le dépôt ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="435eb-124">Consider the repository below:</span></span>

<span data-ttu-id="435eb-125">![Projet existant][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="435eb-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="435eb-126">[**Code source**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="435eb-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="435eb-127">La section suivante décrit plusieurs méthodes pour ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants.</span><span class="sxs-lookup"><span data-stu-id="435eb-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="435eb-128">Remplacer les projets existants par un projet .NET Core multiciblé</span><span class="sxs-lookup"><span data-stu-id="435eb-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="435eb-129">Réorganisez le dépôt de sorte que tous les fichiers *\*.csproj* existants soient supprimés et qu’un seul fichier *\*.csproj* ciblant plusieurs frameworks soit créé.</span><span class="sxs-lookup"><span data-stu-id="435eb-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="435eb-130">Il s’agit d’une option intéressante car un même projet peut être compilé pour différents frameworks.</span><span class="sxs-lookup"><span data-stu-id="435eb-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="435eb-131">Elle permet également de gérer différentes options de compilation et dépendances par framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="435eb-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="435eb-132">![Créer un csproj ciblant plusieurs frameworks][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="435eb-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="435eb-133">[**Code source**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="435eb-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="435eb-134">Les modifications à noter sont :</span><span class="sxs-lookup"><span data-stu-id="435eb-134">Changes to note are:</span></span>
* <span data-ttu-id="435eb-135">Remplacement de *packages.config* et de *\*.csproj* par un nouveau [.csproj *\*.NET Core*][example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="435eb-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="435eb-136">Les packages NuGet sont spécifiés avec `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="435eb-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="435eb-137">Conserver les projets existants et créer un projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="435eb-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="435eb-138">Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.</span><span class="sxs-lookup"><span data-stu-id="435eb-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="435eb-139">![Projet .NET Core avec un projet existant dans un dossier différent][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="435eb-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="435eb-140">[**Code source**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="435eb-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="435eb-141">Les modifications à noter sont :</span><span class="sxs-lookup"><span data-stu-id="435eb-141">Changes to note are:</span></span>
* <span data-ttu-id="435eb-142">Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts.</span><span class="sxs-lookup"><span data-stu-id="435eb-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="435eb-143">Le fait de conserver les projets dans des dossiers distincts vous évite de devoir installer Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="435eb-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="435eb-144">Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.</span><span class="sxs-lookup"><span data-stu-id="435eb-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="435eb-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="435eb-145">See Also</span></span>

<span data-ttu-id="435eb-146">Consultez la [documentation relative au portage vers .NET Core][porting-doc] pour obtenir de l’aide sur la migration vers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="435eb-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projet existant"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Créer un csproj ciblant plusieurs frameworks"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projet .NET Core avec une bibliothèque de classes portable dans un dossier différent"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
