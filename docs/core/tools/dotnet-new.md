---
title: Commande dotnet-new | Microsoft Docs
description: "La commande dotnet-new crée de nouveaux projets .NET Core dans le répertoire actif."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a49fe94ca8f678c614fb7f58767693c73e34c737

---

#<a name="dotnet-new"></a>dotnet-new

> [!WARNING]
> Cette rubrique s'applique aux outils .NET Core Preview 2. Pour la version RC4 des outils .NET Core, consultez la rubrique [dotnet-new (outils .NET Core RC4)](../preview3/tools/dotnet-new.md).

## <a name="name"></a>Nom
`dotnet-new` : Crée un projet .NET Core dans le répertoire actuel.

## <a name="synopsis"></a>Résumé
`dotnet new [--help] [--type] [--lang]`

## <a name="description"></a>Description
La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide et d’obtenir un exemple de code source pour tester l’ensemble des outils de l’interface de ligne de commande (CLI). 

Cette commande est appelée dans le contexte d’un répertoire. Lorsqu’elle est appelée, la commande entraîne la suppression de deux artefacts principaux du répertoire actif : 

1. Un fichier `Program.cs` (ou `Program.fs`) qui contient un exemple de programme « Hello World ».
2. Un fichier `project.json` valide.

Après cela, le projet est prêt à être compilé et/ou édité. 

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-l|--lang <C#|F#>`

Langage du projet. La valeur par défaut est `C#`. Les autres valeurs valides sont `csharp`, `fsharp`, `cs` et `fs`.

`-t|--type`

Type du projet. Les valeurs valides pour C# sont `console`, `web`, `lib` et `xunittest`. Pour F#, seule la valeur `console` est valide. 

## <a name="examples"></a>Exemples

Créez un projet d’application console C# dans le répertoire actif :

`dotnet new` ou `dotnet new --lang c#` 
   
Créez un projet d’application console F# dans le répertoire actif :

`dotnet new --lang f#`
  
Créez un projet d’application console C# ASP.NET Core dans le répertoire actif :

`dotnet new -t web`


<!--HONumber=Feb17_HO2-->


