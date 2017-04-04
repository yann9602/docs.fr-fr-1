---
title: Commande dotnet-add package - CLI .NET Core | Microsoft Docs
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
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 41b46e879056d385ceb3abaec27db974cab812e3
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-add-package"></a>dotnet-add package

## <a name="name"></a>Nom

`dotnet-add package` : Ajoute une référence de package à un fichier projet.

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet. Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet. Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.

Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à ce qui suit :

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

Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files) pour le package référencé.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

`PACKAGE_NAME`

Référence de package à ajouter.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-v|--version <VERSION>`

Version du package.

`-f|--framework <FRAMEWORK>`

Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

`-n|--no-restore`

Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.

`-s|--source <SOURCE>`

Utilise une source de package NuGet spécifique pendant l’opération de restauration.

`--package-directory <PACKAGE_DIRECTORY>`

Restaure le package dans le répertoire spécifié.

## <a name="examples"></a>Exemples

Ajouter un package NuGet `Newtonsoft.Json` à un projet :

`dotnet add package Newtonsoft.Json`

Ajouter une version spécifique d’un package à un projet :

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Ajouter un package à l’aide d’une source NuGet spécifique :

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

