---
title: Commande dotnet-add package - Interface CLI .NET Core
description: "La commande dotnet-add package est une option pratique pour ajouter une référence de package NuGet à un projet."
keywords: dotnet-add, CLI, commande CLI, .NET Core
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40ee7cac969d4752ede66ba8df6ff6cb3f439aec
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-package"></a><span data-ttu-id="20785-104">dotnet-add package</span><span class="sxs-lookup"><span data-stu-id="20785-104">dotnet-add package</span></span>

## <a name="name"></a><span data-ttu-id="20785-105">Nom</span><span class="sxs-lookup"><span data-stu-id="20785-105">Name</span></span>

<span data-ttu-id="20785-106">`dotnet-add package` : Ajoute une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="20785-106">`dotnet-add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="20785-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="20785-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory] [-h|--help]`

## <a name="description"></a><span data-ttu-id="20785-108">Description</span><span class="sxs-lookup"><span data-stu-id="20785-108">Description</span></span>

<span data-ttu-id="20785-109">La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="20785-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="20785-110">Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet.</span><span class="sxs-lookup"><span data-stu-id="20785-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="20785-111">Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="20785-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="20785-112">Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20785-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following:</span></span>

```
Microsoft (R) Build Engine version 15.1.545.13942
Copyright (C) Microsoft Corporation. All rights reserved.

Writing /var/folders/gj/1mgg_4jx7mbdqbhw1kgcpcjr0000gn/T/tmpm0kTMD.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'ToDo.csproj'.
log  : Restoring packages for ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 119ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg 27ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '9.0.1' added to file 'ToDo.csproj'.
```

<span data-ttu-id="20785-113">Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.</span><span class="sxs-lookup"><span data-stu-id="20785-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="20785-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="20785-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="20785-115">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="20785-115">Specifies the project file.</span></span> <span data-ttu-id="20785-116">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="20785-116">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="20785-117">Référence de package à ajouter.</span><span class="sxs-lookup"><span data-stu-id="20785-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="20785-118">Options</span><span class="sxs-lookup"><span data-stu-id="20785-118">Options</span></span>

`-h|--help`

<span data-ttu-id="20785-119">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="20785-119">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="20785-120">Version du package.</span><span class="sxs-lookup"><span data-stu-id="20785-120">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="20785-121">Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="20785-121">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="20785-122">Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="20785-122">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="20785-123">Utilise une source de package NuGet spécifique pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="20785-123">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="20785-124">Restaure le package dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="20785-124">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="20785-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="20785-125">Examples</span></span>

<span data-ttu-id="20785-126">Ajouter un package NuGet `Newtonsoft.Json` à un projet :</span><span class="sxs-lookup"><span data-stu-id="20785-126">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="20785-127">Ajouter une version spécifique d’un package à un projet :</span><span class="sxs-lookup"><span data-stu-id="20785-127">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="20785-128">Ajouter un package à l’aide d’une source NuGet spécifique :</span><span class="sxs-lookup"><span data-stu-id="20785-128">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

