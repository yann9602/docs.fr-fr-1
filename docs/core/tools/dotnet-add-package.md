---
title: Commande dotnet add package - Interface CLI .NET Core
description: "La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet."
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7518ec32d669e64d713e77f687d285279b012967
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-package"></a><span data-ttu-id="d9456-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d9456-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d9456-104">Nom</span><span class="sxs-lookup"><span data-stu-id="d9456-104">Name</span></span>

<span data-ttu-id="d9456-105">`dotnet add package` : Ajoute une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d9456-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d9456-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="d9456-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="d9456-107">Description</span><span class="sxs-lookup"><span data-stu-id="d9456-107">Description</span></span>

<span data-ttu-id="d9456-108">La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d9456-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="d9456-109">Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet.</span><span class="sxs-lookup"><span data-stu-id="d9456-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="d9456-110">Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d9456-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d9456-111">Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d9456-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="d9456-112">Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.</span><span class="sxs-lookup"><span data-stu-id="d9456-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="d9456-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="d9456-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d9456-114">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d9456-114">Specifies the project file.</span></span> <span data-ttu-id="d9456-115">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="d9456-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="d9456-116">Référence de package à ajouter.</span><span class="sxs-lookup"><span data-stu-id="d9456-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="d9456-117">Options</span><span class="sxs-lookup"><span data-stu-id="d9456-117">Options</span></span>

`-h|--help`

<span data-ttu-id="d9456-118">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="d9456-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="d9456-119">Version du package.</span><span class="sxs-lookup"><span data-stu-id="d9456-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d9456-120">Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="d9456-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="d9456-121">Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="d9456-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="d9456-122">Utilise une source de package NuGet spécifique pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="d9456-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="d9456-123">Restaure le package dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="d9456-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="d9456-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="d9456-124">Examples</span></span>

<span data-ttu-id="d9456-125">Ajouter un package NuGet `Newtonsoft.Json` à un projet :</span><span class="sxs-lookup"><span data-stu-id="d9456-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="d9456-126">Ajouter une version spécifique d’un package à un projet :</span><span class="sxs-lookup"><span data-stu-id="d9456-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="d9456-127">Ajouter un package à l’aide d’une source NuGet spécifique :</span><span class="sxs-lookup"><span data-stu-id="d9456-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
