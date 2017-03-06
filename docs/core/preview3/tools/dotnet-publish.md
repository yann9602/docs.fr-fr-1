---
title: Commande dotnet-publish | Microsoft Docs
description: "La commande dotnet-publish publie votre projet .NET Core dans un répertoire."
keywords: "dotnet-publish, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 0d222382640fc239760f8f51c69f1f306674d7ca

---

#<a name="dotnet-publish-net-core-tools-rc4"></a>dotnet-publish (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Preview 2 des outils .NET Core, consultez la rubrique [dotnet-publish](../../tools/dotnet-publish.md).

## <a name="name"></a>Nom

`dotnet-publish` : Place l’application et toutes ses dépendances dans un dossier, pour la préparer à la publication.

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



<!--HONumber=Feb17_HO2-->


