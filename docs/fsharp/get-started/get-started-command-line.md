---
title: "Démarrer avec les outils de ligne de commande avec F #"
description: "Découvrez comment utiliser F # avec l’interface CLI d’inter-plateformes .NET Core."
keywords: visual f#, f#, programmation fonctionnelle, .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: a23d4861ce599f20f37ecd0564a0187e7b9b739f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="be365-104">Prise en main) (F # avec l’interface de ligne de base .NET</span><span class="sxs-lookup"><span data-stu-id="be365-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="be365-105">Cet article décrit comment vous pouvez commencer à utiliser à l’aide de F # sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be365-105">This article covers how you can get started with using F# on .NET Core.</span></span> <span data-ttu-id="be365-106">Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes est appelée par une Application Console.</span><span class="sxs-lookup"><span data-stu-id="be365-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be365-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="be365-107">Prerequisites</span></span>

<span data-ttu-id="be365-108">Pour commencer, vous devez installer le [.NET Core SDK 1.0 ou version ultérieure](https://dot.net/core).</span><span class="sxs-lookup"><span data-stu-id="be365-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="be365-109">Il est inutile pour désinstaller une version précédente du SDK .NET Core, elle prend en charge les installations côte à côte.</span><span class="sxs-lookup"><span data-stu-id="be365-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="be365-110">Cet article suppose que vous savez comment utiliser une ligne de commande et un texte par défaut éditeur.</span><span class="sxs-lookup"><span data-stu-id="be365-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="be365-111">Si vous ne l’utilisez déjà, [Visual Studio Code](https://code.visualstudio.com) est une option intéressante comme un éditeur de texte pour F #.</span><span class="sxs-lookup"><span data-stu-id="be365-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="be365-112">Pour obtenir des fonctionnalités comme IntelliSense, une meilleure mise en surbrillance de syntaxe et bien plus encore, vous pouvez télécharger le [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="be365-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="be365-113">Création d’une Simple Solution à projets multiples</span><span class="sxs-lookup"><span data-stu-id="be365-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="be365-114">Ouvrez une invite de commandes/terminal et utiliser le `dotnet new` commande pour créer le nouveau fichier de solution appelé `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="be365-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="be365-115">La structure de répertoire suivant est générée suite à l’exécution de la commande :</span><span class="sxs-lookup"><span data-stu-id="be365-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="be365-116">Remplacez les répertoires par *FSNetCore* et commencer à ajouter des projets dans le dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="be365-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="be365-117">L’écriture d’une bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="be365-117">Writing a Class library</span></span>

<span data-ttu-id="be365-118">Utilisez le `dotnet new` de commande, créez un projet de bibliothèque de classes dans le **src** dossier nommé bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="be365-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="be365-119">La structure de répertoire suivante est générée à la suite de l’exécution de la commande :</span><span class="sxs-lookup"><span data-stu-id="be365-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="be365-120">Remplacez le contenu de `Library.fs` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="be365-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="be365-121">Ajoutez le package Newtonsoft.Json NuGet pour le projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="be365-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="be365-122">Ajouter le `Library` de projet pour le `FSNetCore` à l’aide de la solution la `dotnet sln add` commande :</span><span class="sxs-lookup"><span data-stu-id="be365-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="be365-123">Restaurer les dépendances de NuGet, `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) et exécutez `dotnet build` pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="be365-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="be365-124">Écriture d’une Application Console qui utilise la bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="be365-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="be365-125">Utilisez le `dotnet new` de commande, créer une application de Console dans le **src** dossier nommé application.</span><span class="sxs-lookup"><span data-stu-id="be365-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="be365-126">La structure de répertoire suivante est générée à la suite de l’exécution de la commande :</span><span class="sxs-lookup"><span data-stu-id="be365-126">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="be365-127">Modification `Program.fs` pour :</span><span class="sxs-lookup"><span data-stu-id="be365-127">Change `Program.fs` to:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv = 
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

<span data-ttu-id="be365-128">Ajoutez une référence à la `Library` à l’aide de projet `dotnet add reference`.</span><span class="sxs-lookup"><span data-stu-id="be365-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="be365-129">Ajouter le `App` de projet pour le `FSNetCore` à l’aide de la solution la `dotnet sln add` commande :</span><span class="sxs-lookup"><span data-stu-id="be365-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="be365-130">Restaurer les dépendances de NuGet, `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) et exécutez `dotnet build` pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="be365-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="be365-131">Remplacez le répertoire pour la `src/App` projet de console et exécuter le projet en passant `Hello World` en tant qu’arguments.</span><span class="sxs-lookup"><span data-stu-id="be365-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="be365-132">Vous devez voir les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="be365-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]