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
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e480c32faa22859de74e06f3a199fba1c0720c46

---

#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Nom

`dotnet-publish` : Package l’application et toutes ses dépendances dans un dossier, en préparation de sa publication

## <a name="synopsis"></a>Résumé

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--output]  
    [--version-suffix] [--configuration]`

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. 

Selon le type d’application portable, le répertoire obtenu contiendra les éléments suivants :

1. *Déploiement dépendant du framework* : code en langage intermédiaire de l’application et toutes les dépendances gérées de l’application.
2. *Déploiement autonome* : même chose que ci-dessus, mais avec l’intégralité du runtime pour la plateforme ciblée.

Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

## <a name="options"></a>Options

`[project]` 

Projet à publier. Si `[project]` n’est pas spécifié, la valeur utilisée par défaut sera le répertoire actif. 

`-h|--help`

Affiche une aide brève pour la commande.  

`-f|--framework <FRAMEWORK>`

Publie l’application pour un identificateur de framework donné. 

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Pour connaître les identificateurs de runtime que vous pouvez utiliser, consultez le [catalogue des identificateurs de runtime ](../../rid-catalog.md).

`-o|--output <OUTPUT_PATH>`

Spécifiez le chemin du répertoire. Si aucune valeur n’est spécifiée, il s’agira par défaut de *_./bin/[configuration]/[framework]/_* pour les applications portables ou de *_./bin/[configuration]/[framework]/[runtime]_* pour les déploiements autonomes.

`--version-suffix [VERSION_SUFFIX]`

Définit par quoi `*` doit être remplacé dans le champ de version du fichier projet.

`-c|--configuration [Debug|Release]`

Configuration à utiliser lors de la publication. La valeur par défaut est `Debug`.

## <a name="examples"></a>Exemples

Publiez une application :

`dotnet publish`

Publiez l’application à l’aide du fichier projet spécifié :

`dotnet publish ~/projects/app1/app1.csproj`
    
Publiez l’application actuelle à l’aide du framework `netcoreapp1.0` :

`dotnet publish --framework netcoreapp1.0`
    
Publiez l’application actuelle à l’aide du framework `netcoreapp1.0` et du runtime pour `OS X 10.10` (l’identificateur de runtime doit se trouver dans le fichier projet) :

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>Voir aussi
* [Frameworks](../../../standard/frameworks.md)
* [Catalogue d’identificateurs de runtime (RID)](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


