---
title: Commande dotnet-publish | SDK .NET Core
description: "La commande dotnet-publish publie votre projet .NET Core dans un répertoire."
keywords: "dotnet-publish, CLI, commande CLI, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 2b00a2c6da73c2252997b63aca8fc475cac8999f

---

#<a name="dotnetpublish"></a>dotnet-publish

## <a name="name"></a>Nom

`dotnet-publish` : Package l’application et toutes ses dépendances dans un dossier, en préparation de sa publication

## <a name="synopsis"></a>Résumé

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--build-base-path] [--output]  
    [--version-suffix] [--configuration] [--native-subdirectory] [--no-build]`

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier [project.json](project-json.md) et publie l’ensemble de fichiers obtenus dans un répertoire. 

Selon le type d’application portable, le répertoire obtenu contiendra les éléments suivants :

1. *Application portable* - code en langage intermédiaire de l’application et toutes les dépendances gérées de l’application.
    * *Application portable avec dépendances natives* - même chose que ci-dessus, mais avec un sous-répertoire pour la plateforme prise en charge de chaque dépendance native. 
2. *Application autonome* - même chose que ci-dessus, mais avec l’intégralité du runtime pour la plateforme ciblée.

Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

## <a name="options"></a>Options

`[project]` 

Projet à publier. Si `[project]` n’est pas spécifié, la valeur utilisée par défaut sera le répertoire actif. Cette valeur peut être le chemin du fichier [project.json](project-json.md) ou du répertoire du projet qui contient le fichier [project.json](project-json.md). Si aucun fichier [project.json](project-json.md) n’est trouvé, `dotnet publish` génère une erreur. 

`-h|--help`

Affiche une aide brève pour la commande.  

`-f|--framework <FRAMEWORK>`

Publie l’application pour un identificateur de framework donné. Si aucun identificateur n’est spécifié, l’identificateur du [project.json](project-json.md#frameworks) est choisi par défaut. Si aucun framework valide n’est trouvé, la commande génère une erreur. Si plusieurs frameworks valides sont trouvés, la commande publie l’application pour tous les frameworks valides. 

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Pour connaître les identificateurs de runtime que vous pouvez utiliser, consultez le [catalogue des identificateurs de runtime ](../rid-catalog.md).

`-b|--build-base-path <OUTPUT_DIRECTORY>`

Répertoire dans lequel placer les sorties temporaires.

`-o|--output <OUTPUT_PATH>`

Spécifiez le chemin du répertoire. Si aucune valeur n’est spécifiée, il s’agira par défaut de *_./bin/[configuration]/[framework]/_* pour les applications portables ou de *_./bin/[configuration]/[framework]/[runtime]_* pour les déploiements autonomes.

`--version-suffix [VERSION_SUFFIX]`

Définit par quoi `*` doit être remplacé dans le champ de version du fichier project.json.

`-c|--configuration [Debug|Release]`

Configuration à utiliser lors de la publication. La valeur par défaut est `Debug`.

`[--native-subdirectory]` Mécanisme temporaire permettant d’inclure dans la sortie les sous-répertoires des ressources natives des packages de dépendances. 

`[--no-build]` Ne génère pas les projets avant la publication.

## <a name="examples"></a>Exemples

Publiez une application à l’aide du framework trouvé dans `project.json`. Si `project.json` contient le nœud [runtimes](project-json.md#runtimes), publiez l’application pour l’identificateur de runtime de la plateforme actuelle.

`dotnet publish`

Publiez l’application à l’aide du [project.json](project-json.md) spécifié :

`dotnet publish ~/projects/app1/project.json`
    
Publiez l’application actuelle à l’aide du framework `netcoreapp1.0` :

`dotnet publish --framework netcoreapp1.0`
    
Publiez l’application actuelle à l’aide du framework `netcoreapp1.0` et du runtime pour `OS X 10.10` (l’identificateur de runtime doit se trouver sous le nœud [runtimes](project-json.md#runtimes) `project.json`) :

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>Voir aussi
* [Frameworks](../../standard/frameworks.md)
* [Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)


<!--HONumber=Nov16_HO1-->


