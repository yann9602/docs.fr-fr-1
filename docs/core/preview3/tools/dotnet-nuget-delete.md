---
title: Commande dotnet-nuget-delete | Microsoft Docs
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
keywords: dotnet-nuget-delete, CLI, commande CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 787b1427b1064943570cbc361042ab2f20d11088
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nom 
`dotnet-nuget-delete` -Supprime ou retire un package du serveur. 

## <a name="synopsis"></a>Résumé

`dotnet nuget delete [<package_name> <package_version>] 
    [--help] [--source] [--non-interactive] 
    [--api-key] [--force-english-output] [--verbosity] [--config-file]`

## <a name="description"></a>Description

La commande `dotnet nuget delete` supprime ou retire un package du serveur. Pour NuGet.org, l’action consiste à supprimer le package de la liste.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.  

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Les URL prises en charge pour nuget.org incluent `http://www.nuget.org`, `http://www.nuget.org/api/v3` et `http://www.nuget.org/api/v2/package`. Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).

`--non-interactive`

Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--force-english-output`

Oblige la sortie de la ligne de commande à être en anglais.

`--verbosity <LEVEL>`

Affiche la quantité de détails définie dans la sortie. Le niveau peut être `normal`, `quiet` ou `detailed`.

`--config-file <FILE>`

Fichier de configuration NuGet utilisé spécifiquement pour cette commande, avec remplacement des autres fichiers de configuration trouvés par la découverte des fichiers de configuration standard et chaînage du processus. Le chemin peut être absolu ou relatif.
Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ).

## <a name="examples"></a>Exemples

Supprime la version 1.0 du package MyPackage :

`dotnet nuget delete MyPackage 1.0` 

Supprime la version 1.0 du package MyPackage sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :

`dotnet nuget delete MyPackage 1.0 --non-interactive`

Supprime la version 1.0 du package MyPackage en spécifiant un fichier de configuration personnalisé *./config/My.Config* :

`dotnet nuget delete MyPackage 1.0 --config-file ./config/My.Config`

Supprime la version 1.0 du package MyPackage, avec un maximum de commentaires :

`dotnet nuget delete MyPackage 1.0 --verbosity detailed`

