---
title: "Démarrer avec les outils de ligne de commande avec F #"
description: "Découvrez comment utiliser F # sur un système d’exploitation (Windows, MacOS, Linux) avec l’interface CLI d’inter-plateformes .NET Core."
keywords: visual f#, f#, programmation fonctionnelle, .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Prise en main) (F # avec l’interface de ligne de base .NET

Cet article décrit comment vous pouvez commencer par n’importe quel système d’exploitation (Windows, Mac OS ou Linux) à l’aide de F # avec l’interface de ligne de base de .NET. Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes est appelée par une Application Console.

## <a name="prerequisites"></a>Prérequis

Pour commencer, vous devez installer le [.NET Core SDK 1.0 ou version ultérieure](https://dot.net/core). Il est inutile pour désinstaller une version précédente du SDK .NET Core, elle prend en charge les installations côte à côte.

Cet article suppose que vous savez comment utiliser une ligne de commande et un texte par défaut éditeur. Si vous ne l’utilisez déjà, [Visual Studio Code](https://code.visualstudio.com) est une option intéressante comme un éditeur de texte pour F #. Pour obtenir des fonctionnalités comme IntelliSense, une meilleure mise en surbrillance de syntaxe et bien plus encore, vous pouvez télécharger le [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="building-a-simple-multi-project-solution"></a>Création d’une Simple Solution à projets multiples

Ouvrez une invite de commandes/terminal et utiliser le `dotnet new` commande pour créer le nouveau fichier de solution appelé `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

La structure de répertoire suivant est générée suite à l’exécution de la commande :

```
FSNetCore
    ├── FSNetCore.sln
```

Remplacez les répertoires par *FSNetCore* et commencer à ajouter des projets dans le dossier de solution.
 
### <a name="writing-a-class-library"></a>L’écriture d’une bibliothèque de classes

Utilisez le `dotnet new` de commande, créez un projet de bibliothèque de classes dans le **src** dossier nommé bibliothèque. 

```bash
dotnet new lib -lang F# -o src/Library 
```

La structure de répertoire suivante est générée à la suite de l’exécution de la commande :

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Remplacez le contenu de `Library.fs` par le code suivant :

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Ajoutez le package Newtonsoft.Json NuGet pour le projet de bibliothèque.

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ajouter le `Library` de projet pour le `FSNetCore` à l’aide de la solution la `dotnet sln add` commande :

```bash
dotnet sln add src/Library/Library.fsproj
```

Restaurer les dépendances de NuGet, `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) et exécutez `dotnet build` pour générer le projet.

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>Écriture d’une Application Console qui utilise la bibliothèque de classes

Utilisez le `dotnet new` de commande, créer une application de Console dans le **src** dossier nommé application. 

```bash
dotnet new console -lang F# -o src/App 
```

La structure de répertoire suivante est générée à la suite de l’exécution de la commande :

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

Modification `Program.fs` pour :

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

Ajoutez une référence à la `Library` à l’aide de projet `dotnet add reference`.

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ajouter le `App` de projet pour le `FSNetCore` à l’aide de la solution la `dotnet sln add` commande :

```bash
dotnet sln add src/App/App.fsproj
```

Restaurer les dépendances de NuGet, `dotnet restore` ([voir la Remarque](#dotnet-restore-note)) et exécutez `dotnet build` pour générer le projet.

Remplacez le répertoire pour la `src/App` projet de console et exécuter le projet en passant `Hello World` en tant qu’arguments.

```bash
cd src/App
dotnet run Hello World
``` 

Vous devez voir les résultats suivants :

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
