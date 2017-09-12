---
title: Scripts dotnet-install
description: "Découvrez les scripts dotnet-install pour installer les outils CLI .NET Core et le runtime partagé."
keywords: dotnet-install, scripts dotnet-install, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/28/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.translationtype: HT
ms.sourcegitcommit: c6e199800a86bc8b275fed4e3ba3ea6f77c7d2fa
ms.openlocfilehash: 92c2b4dcd446d3bf68783768db25ad55b14fac44
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---

# <a name="dotnet-install-scripts-reference"></a>Documentation sur les scripts dotnet-install

## <a name="name"></a>Name

`dotnet-install.ps1` | `dotnet-install.sh` : script utilisé pour installer les outils .NET Core CLI et le runtime partagé.

## <a name="synopsis"></a>Résumé

Windows :

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

Mac OS/Linux :

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Description

Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur du SDK .NET Core, qui inclut les outils .NET Core CLI et le runtime partagé.

Nous vous recommandons d’utiliser la version stable hébergée sur le [site web principal de .NET Core](https://dot.net). Les chemins d’accès directs aux scripts sont :

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)

La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur. Il existe deux scripts : un script PowerShell qui fonctionne sous Windows. L’autre script est un script bash qui fonctionne sur Linux/macOS. Les deux scripts ont le même comportement. Comme le script bash lit également les commutateurs PowerShell, vous pouvez utiliser ces derniers avec le script sur les systèmes Linux/macOS. 

Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`. Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK). Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `--shared-runtime`. 

Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active. Remplacez ce comportement par défaut en spécifiant l’argument `--no-path`. 

Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.

Vous pouvez installer une version spécifique à l’aide de l’argument `--version`. La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232). Si aucune valeur n’est spécifiée, la version `latest` est utilisée.

## <a name="options"></a>Options

`-Channel <CHANNEL>`

Spécifie le canal source pour l’installation. Les valeurs possibles sont :

- `Current` - Version actuelle
- `LTS` - Canal de prise en charge à long terme (version prise en charge actuelle)
- Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`)
- Nom de la branche [par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` pour la version la plus récente de la branche `master` (versions nocturnes « bleeding edge »)]

La valeur par défaut est `LTS`. Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la rubrique [Cycle de prise en charge de .NET Core](https://www.microsoft.com/net/core/support).

`-Version <VERSION>`

Représente une version spécifique. Les valeurs possibles sont :

- `latest` - Dernière version sur le canal (utilisée avec l’option `-Channel`)
- `coherent` - Dernière version cohérente sur le canal ; utilise la dernière combinaison de packages stable (utilisée avec les options `-Channel` de nom de branche)
- Version en trois parties au format X.Y.Z représentant une version spécifique ; remplace l’option `-Channel`. Par exemple :`2.0.0-preview2-006120`

Si aucune valeur n'est spécifiée, la valeur utilisée par défaut pour `-Version` est `latest`.

`-InstallDir <DIRECTORY>`

Spécifie le chemin d’accès de l’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est *% LocalAppData%\.dotnet*. Remarque : Les fichiers binaires sont placés directement dans le répertoire.

`-Architecture <ARCHITECTURE>`

Architecture des fichiers binaires .NET Core à installer. Les valeurs possibles sont `auto`, `x64` et `x86`. La valeur par défaut est `auto`, qui représente l’architecture de système d’exploitation en cours d’exécution.

`-SharedRuntime`

S’il est défini, ce commutateur limite l’installation au runtime partagé. La totalité du SDK n’est pas installée.

`-DryRun`

Si cette option est définie, le script n’effectue pas l’installation, mais affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée. Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération. Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.

`-NoPath`

Si cette option est définie, le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle. Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.

`-AzureFeed`

Spécifie l’URL du flux Azure à utiliser par ce programme d’installation. Il n’est pas recommandé de modifier cette valeur. La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web. (valide uniquement pour Windows)

`--verbose`

Affiche les informations de diagnostic.

`--help`

Affiche l’aide pour le script.

## <a name="examples"></a>Exemples

Installez la dernière version LTS (Long Term Support) à l’emplacement par défaut :

Windows :

`./dotnet-install.ps1 -Channel LTS`

Mac OS/Linux :

`./dotnet-install.sh --channel LTS`

Installez la dernière version depuis le canal 2.0 à l’emplacement spécifié :

Windows :

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

Mac OS/Linux :

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Installez la version 1.1.0 du runtime partagé :

Windows :

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

Mac OS/Linux :

`./dotnet-install.sh --shared-runtime --version 1.1.0`

## <a name="see-also"></a>Voir aussi

[Versions de .NET Core](https://github.com/dotnet/core/releases)   
[Archive de téléchargement de .NET Core Runtime et du Kit SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

