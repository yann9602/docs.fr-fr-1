---
title: Commande dotnet-build | SDK .NET Core
description: "La commande dotnet-build permet de générer un projet et l’ensemble de ses dépendances."
keywords: dotnet-build, CLI, commande CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 04c4d77b31bf4a1bdb425d837c490440e7312e57

---

#<a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>Nom 
dotnet-build -- Permet de générer un projet et l’ensemble de ses dépendances. 

## <a name="synopsis"></a>Résumé

`dotnet build [--help] [--output]  [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`

## <a name="description"></a>Description

La commande `dotnet build` permet de générer plusieurs fichiers sources à partir d’un projet source et de ses dépendances, sous la forme d’un fichier binaire. Par défaut, le fichier binaire obtenu est en langage intermédiaire (IL) et possède une extension DLL. 
`dotnet build` dépose également un fichier `\*.deps` qui décrit ce dont l’ordinateur hôte a besoin pour exécuter l’application.  

La génération nécessite l’existence d’un fichier de ressource (fichier qui répertorie toutes les dépendances de votre application), ce qui signifie que vous devez exécuter [`dotnet restore`](dotnet-restore.md) avant de générer votre code.

Avant le début de la compilation, le verbe `build` analyse le projet et ses dépendances dans le cadre de vérifications de sécurité incrémentielle.
Si le résultat de toutes les vérifications est positif, la génération se poursuit avec la compilation incrémentielle du projet et de ses dépendances. Dans le cas contraire, elle revient à la compilation non incrémentielle. Grâce à un indicateur de profil, les utilisateurs peuvent choisir de recevoir des informations supplémentaires concernant l’amélioration de la durée de leurs générations.

Pour générer une application exécutable au lieu d’une bibliothèque, vous devez définir la propriété `<OutputType>` :

```xml
<PropertyGroup>
    <OutputType>Exe</OutputType>
</PropertyGroup>
```

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel placer les fichiers binaires générés. Vous devez également définir `--framework` lorsque vous spécifiez cette option.

`-f|--framework <FRAMEWORK>`

Compile pour un framework spécifique. Le framework doit être défini dans le [fichier projet](csproj.md).

`-c|--configuration [Debug|Release]`

Définit une configuration dans laquelle effectuer la génération.  Si aucune valeur n’est spécifiée, la valeur utilisée par défaut est `Debug`.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Runtime cible de la génération. Pour connaître les identificateurs de runtime que vous pouvez utiliser, consultez le [catalogue des identificateurs de runtime ](../../rid-catalog.md). 

`--version-suffix [VERSION_SUFFIX]`

Définit par quoi `*` doit être remplacé dans le champ de version du fichier projet. Le format respecte les instructions de version de NuGet. 

`--build-profile`

Affiche les problèmes liés aux vérifications de sécurité incrémentielle que les utilisateurs doivent résoudre pour que la compilation incrémentielle soit activée automatiquement.

`--no-incremental`

Marque la build comme unsafe pour la génération incrémentielle. Cela désactive la compilation incrémentielle et force une régénération du graphique de dépendance du projet.

`--no-dependencies`

Ignore les références entre projets et génère uniquement le projet racine spécifié pour la génération.

## <a name="examples"></a>Exemples

Générer un projet et ses dépendances :

`dotnet build`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet build --configuration Release`

Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 16.04) :

`dotnet build --runtime ubuntu.16.04-x64`



<!--HONumber=Nov16_HO3-->


