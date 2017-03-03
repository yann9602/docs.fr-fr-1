---
title: Commande dotnet-nuget-push | Microsoft Docs
description: "La commande dotnet-nuget-push exécute un push d’un package sur le serveur et le publie."
keywords: dotnet-nuget-push, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: dcc89fd24e23e624c4bcf90a8200b4e655af6dd6
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-nuget-push"></a>dotnet-nuget-push

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nom 
`dotnet-nuget-push` - Exécute un push d’un package sur le serveur et le publie. 

## <a name="synopsis"></a>Résumé

`dotnet nuget push [<package>] [--help] [--source] [--symbols-source] 
    [--timeout] [--api-key] [--symbol-api-key] [--disable-buffering] [--no-symbols] 
    [--force-english-output] [--config-file] [--verbosity]`

## <a name="description"></a>Description

La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie. La commande push utilise les informations serveur et d’identification trouvées dans la chaîne de fichiers de configuration ou le fichier de configuration NuGet du système. Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ). La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Cette option est obligatoire, sauf si la valeur de configuration DefaultPushSource est définie dans le fichier de configuration de NuGet.

`--symbols-source <SOURCE>`

Spécifie l’URL du serveur de symboles.

`-t|--timeout <TIMEOUT>`

Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur. La valeur par défaut est 300 secondes (5 minutes). La valeur 0 équivaut également à cette valeur par défaut.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--symbol-api-key <API_KEY>`

Clé d’API pour le serveur de symboles.

`-d|--disable-buffering`

Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.

`-n|--no-symbols`

N’exécute pas un push de symboles (même s’ils sont présents).

`--force-english-output`

Oblige toutes les sorties enregistrées à être en anglais. Outre la possibilité de produire une sortie en anglais sur un ordinateur non anglais, la cohérence entre les plateformes fournie par cette option est une fonctionnalité utile pour les outils automatisés qui récupèrent du texte des journaux.

`--config-file <FILE>`

Fichier de configuration NuGet utilisé spécifiquement pour cette commande, avec remplacement des autres fichiers de configuration trouvés par la découverte des fichiers de configuration standard et chaînage du processus. Le chemin peut être absolu ou relatif.
Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ). 

`--verbosity <LEVEL>`

Affiche la quantité de détails définie dans la sortie. Le niveau peut être `normal`, `quiet` ou `detailed`.

## <a name="examples"></a>Exemples

Exécute un push de foo.nupkg vers la source de push par défaut, en fournissant la clé d’API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Exécute un push de foo.nupkg vers la source de push personnalisée `http://customsource`, en fournissant la clé d’API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/` 

Exécute un push de foo.nupkg vers la source de push par défaut :

`dotnet nuget push foo.nupkg` 

Exécute un push de foo.symbols.nupkg vers la source de symboles par défaut :

`dotnet nuget push foo.symbols.nupkg`

Exécute un push de foo.nupkg vers la source de push par défaut, en spécifiant un délai d’attente de 360 secondes :

`dotnet nuget push foo.nupkg --timeout 360`

Exécute un push de tous les fichiers .nupkg du répertoire actif vers la source de push par défaut :

`dotnet nuget push *.nupkg`

Exécute un push de tous les fichiers .nupkg du répertoire actif vers la source de push par défaut, en spécifiant un fichier de configuration personnalisé *./config/My.Config* :

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

Exécute un push de tous les fichiers .nupkg du répertoire actif vers la source de push par défaut, avec le maximum de commentaires :

`dotnet nuget push *.nupkg --verbosity detailed`

