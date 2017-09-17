---
title: Commande dotnet add package - Interface CLI .NET Core
description: "La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet."
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 54fe434c44c9354ae16ae096fe3496ee0134f6e0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-add-package"></a>dotnet add package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet add package` : Ajoute une référence de package à un fichier projet.

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a>Description

La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet. Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet. Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.

Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.

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

Affiche une aide élémentaire de la commande.

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

