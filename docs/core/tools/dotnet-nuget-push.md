---
title: Commande dotnet nuget push - Interface CLI .NET Core
description: "La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: dc4250ab7417c9f19babdf37c556daf7c3bd6a81
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet nuget push` - Exécute un push d’un package sur le serveur et le publie.

## <a name="synopsis"></a>Résumé

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie. La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système. Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ). La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.

## <a name="arguments"></a>Arguments

`ROOT`

Spécifiez le chemin d’accès au package et votre clé API pour effectuer une transmission de type push du package vers le serveur.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.

`--symbol-source <SOURCE>`

Spécifie l’URL du serveur de symboles.

`-t|--timeout <TIMEOUT>`

Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur. La valeur par défaut est 300 secondes (5 minutes). Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--symbol-api-key <API_KEY>`

Clé d’API pour le serveur de symboles.

`-d|--disable-buffering`

Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.

`-n|--no-symbols`

N’envoie pas les symboles (même s’ils sont présents).

`--force-english-output`

Force toutes les sorties enregistrées à être en anglais.

## <a name="examples"></a>Exemples

Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut, en fournissant une clé API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Effectuer une transmission de type push de *foo.nupkg* vers la source de push personnalisée `http://customsource`, en fournissant une clé API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut :

`dotnet nuget push foo.nupkg`

Effectuer une transmission de type push de *foo.symbols.nupkg* vers la source de symboles par défaut :

`dotnet nuget push foo.symbols.nupkg`

Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut, en spécifiant un délai d’attente de 360 secondes :

`dotnet nuget push foo.nupkg --timeout 360`

Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut :

`dotnet nuget push *.nupkg`

Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut, en spécifiant un fichier de configuration personnalisé *./config/My.Config* :

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut, avec le maximum de commentaires :

`dotnet nuget push *.nupkg --verbosity detailed`
