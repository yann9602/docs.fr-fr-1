---
title: Commande dotnet-new | .NET Core
description: "La commande dotnet-new crée de nouveaux projets .NET Core dans le répertoire actif."
keywords: "dotnet-new, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 49f0a5e9b385c09a31cc463a77a74894b4304792

---

#<a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>Nom
dotnet-new -- crée un projet .NET Core dans le répertoire actif

## <a name="synopsis"></a>Résumé
`dotnet new [--help] [--type] [--lang]`

## <a name="description"></a>Description
La commande `dotnet new` offre un moyen pratique d’initialiser un projet .NET Core valide et d’obtenir un exemple de code source pour tester l’ensemble des outils de l’interface de ligne de commande (CLI). 

Cette commande est appelée dans le contexte d’un répertoire. Quand elle est appelée, la commande entraîne le dépôt de deux artefacts principaux dans le répertoire actif : 

1. Un fichier `Program.cs` (ou `Program.fs`) qui contient un exemple de programme « Hello World ».
2. Un fichier de projet csproj valide.

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


<!--HONumber=Nov16_HO3-->


