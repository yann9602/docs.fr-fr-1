---
title: Commande dotnet nuget push - Interface CLI .NET Core
description: "La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 6721615e4df820ab50ea4f79fbba30daeffe8165
ms.contentlocale: fr-fr
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet nuget push` - Envoie (push) un package sur le serveur et le publie.

## <a name="synopsis"></a>Résumé

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet nuget push` envoie (push) un package sur le serveur et le publie. La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système. Pour plus d’informations sur les fichiers de configuration, consultez [Configuration du comportement de NuGet](/nuget/consume-packages/configuring-nuget-behavior). La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.

## <a name="arguments"></a>Arguments

`ROOT`

Spécifiez le chemin du package et votre clé API pour envoyer (push) le package au serveur.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide élémentaire de la commande.

`-s|--source <SOURCE>`

Spécifie l’URL du serveur. Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.

`--symbols-source <SOURCE>`

Spécifie l’URL du serveur de symboles.

`-t|--timeout <TIMEOUT>`

Spécifie le délai d’attente, en secondes, pour l’envoi (push) à un serveur. La valeur par défaut est 300 secondes (5 minutes). Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.

`-k|--api-key <API_KEY>`

Clé d’API pour le serveur.

`--symbol-api-key <API_KEY>`

Clé d’API pour le serveur de symboles.

`-d|--disable-buffering`

Désactive la mise en mémoire tampon pendant l’envoi (push) à un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.

`-n|--no-symbols`

N’envoie pas les symboles (même s’ils sont présents).

`--force-english-output`

Force toutes les sorties enregistrées à être en anglais.

## <a name="examples"></a>Exemples

Envoie (push) *foo.nupkg* à la source d’envoi (push) par défaut, en fournissant une clé API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Envoie (push) *foo.nupkg* à la source d’envoi (push) personnalisée `http://customsource`, en fournissant une clé API :

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Envoie (push) *foo.nupkg* à la source d’envoi (push) par défaut :

`dotnet nuget push foo.nupkg`

Envoie (push) *foo.symbols.nupkg* à la source de symboles par défaut :

`dotnet nuget push foo.symbols.nupkg`

Envoie (push) *foo.nupkg* à la source d’envoi (push) par défaut, en spécifiant un délai d’attente de 360 secondes :

`dotnet nuget push foo.nupkg --timeout 360`

Envoie (push) tous les fichiers *.nupkg* du répertoire actif vers la source d’envoi (push) par défaut :

`dotnet nuget push *.nupkg`

Envoie (push) tous les fichiers *.nupkg* du répertoire actif vers la source d’envoi (push) par défaut, en spécifiant un fichier de configuration personnalisé *./config/My.Config* :

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

Envoie (push) tous les fichiers *.nupkg* du répertoire actif à la source d’envoi (push) par défaut, avec le maximum de commentaires :

`dotnet nuget push *.nupkg --verbosity detailed`

