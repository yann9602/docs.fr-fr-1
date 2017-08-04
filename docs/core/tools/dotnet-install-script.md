---
title: Scripts dotnet-install
description: "Découvrez les scripts dotnet-install pour installer les outils CLI .NET Core et le runtime partagé."
keywords: dotnet-install, scripts dotnet-install, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/10/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8af168e96f8f5b57626b126135d8b5e509fbb059
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-install-scripts-reference"></a>Documentation sur les scripts dotnet-install

## <a name="name"></a>Nom

`dotnet-install.ps1` | `dotnet-install.sh` : script utilisé pour installer les outils de l’interface de ligne de commande (CLI) .NET Core et le runtime partagé.

## <a name="synopsis"></a>Résumé

Windows :

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]`

Mac OS/Linux :

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

## <a name="description"></a>Description

Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé. Vous pouvez télécharger les scripts à partir du [référentiel GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain). 

La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur. Il existe deux scripts : un script PowerShell qui fonctionne sous Windows. L’autre script est un script bash fonctionnant sous Linux/OS X. Les deux scripts ont le même comportement. Le script bash lit également les commutateurs PowerShell, pour vous permettre d’utiliser les commutateurs PowerShell avec le script sur les systèmes Linux/OS X. 

Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`. Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK). Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `--shared-runtime`. 

Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active. Remplacez ce comportement par défaut en spécifiant l’argument `--no-path`. 

Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.

Vous pouvez installer une version spécifique à l’aide de l’argument `--version`. La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232). Si vous ne spécifiez pas de version, la valeur utilisée par défaut sera celle du premier fichier [global.json](global-json.md) trouvé dans la hiérarchie au-dessus du dossier dans lequel le script est appelé, et qui contient la propriété `version`. Si ce fichier n’est pas présent, la version la plus récente sera utilisée.

Vous pouvez également utiliser ce script pour obtenir le SDK ou les fichiers binaires de débogage de runtime partagé avec les symboles de débogage, à l’aide de l’argument `--debug`. Si vous n’effectuez pas cette opération lors de la première installation et réalisez ultérieurement que vous avez besoin des symboles de débogage, vous pouvez réexécuter le script avec l’argument `--debug` et la version du Kit de développement logiciel (SDK) installé pour obtenir les symboles de débogage. 

## <a name="options"></a>Options

Remarque : les options diffèrent d’une implémentation de script à l’autre. 

### <a name="powershell-windows"></a>PowerShell (Windows)

`-Channel <CHANNEL>`

Spécifie le canal source pour l’installation. Les valeurs possibles sont :

- `Current` - Version actuelle
- `LTS` - Canal de prise en charge à long terme (version prise en charge actuelle)
- Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`)
- Nom de la branche [par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` pour la version la plus récente de la branche `master` (versions nocturnes « bleeding edge »)]

La valeur par défaut est `LTS`. Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la rubrique [Cycle de prise en charge de .NET Core](https://www.microsoft.com/net/core/support).

`-Version <VERSION>`

Représente une version de build sur le canal source (voir l’option `-Channel`). Les valeurs possibles sont :

- `latest` - Dernière build sur le canal
- `coherent` - Dernière build cohérente sur le canal ; utilise la dernière combinaison de packages stable
- Version en trois parties au format X.Y.Z représentant une version de build spécifique (par exemple, `1.0.x`, où `x` représente la version corrective ; ou une build spécifique, par exemple `2.0.0-preview2-006120`)

Si elle n’est pas spécifiée, la valeur utilisée par défaut pour `-Version` est celle du premier [global.json](global-json.md) qui contient le membre `version`. En l’absence de ce membre, la valeur par défaut de `-Version` est `latest`.

`-InstallDir <DIRECTORY>`

Spécifie le chemin d’accès de l’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est *% LocalAppData%\.dotnet*. Remarque : Les fichiers binaires sont placés directement dans le répertoire.

`-Architecture <ARCHITECTURE>`

Architecture des fichiers binaires .NET Core à installer. Les valeurs possibles sont `auto`, `x64` et `x86`. La valeur par défaut est `auto`, qui représente l’architecture de système d’exploitation en cours d’exécution.

`-SharedRuntime`

S’il est défini, ce commutateur limite l’installation au runtime partagé. La totalité du SDK n’est pas installée.

`-DebugSymbols` (voir la REMARQUE)

Si cette option est définie, le programme d’installation inclut les symboles de débogage dans l’installation.

> [!NOTE]
> Le commutateur `-DebugSymbols` n’est pas actuellement disponible, mais cela est prévu dans une prochaine version.

`-DryRun`

Si cette option est définie, le script n’effectue pas l’installation, mais affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée. Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération. Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.

`-NoPath`

Si cette option est définie, le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle. Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.

`-AzureFeed`

Spécifie l’URL du flux Azure à utiliser par ce programme d’installation. Il n’est pas recommandé de modifier cette valeur. La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web.

### <a name="bash-macoslinux"></a>Interpréteur de commandes (Mac OS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

`-Channel <CHANNEL>`

Spécifie le canal source pour l’installation. Les valeurs possibles sont :

- `Current` - Version actuelle
- `LTS` - Canal de prise en charge à long terme (version prise en charge actuelle)
- Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`)
- Nom de la branche [par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` pour la version la plus récente de la branche `master` (versions nocturnes « bleeding edge »)]

La valeur par défaut est `LTS`. Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la rubrique [Cycle de prise en charge de .NET Core](https://www.microsoft.com/net/core/support).

`-Version <VERSION>`

Représente une version de build sur le canal source (voir l’option `-Channel`). Les valeurs possibles sont :

- `latest` - Dernière build sur le canal
- `coherent` - Dernière build cohérente sur le canal ; utilise la dernière combinaison de packages stable
- Version en trois parties au format X.Y.Z représentant une version de build spécifique (par exemple, `1.0.x`, où `x` représente la version corrective ; ou une build spécifique, par exemple `2.0.0-preview2-006120`)

Si elle n’est pas spécifiée, la valeur utilisée par défaut pour `-Version` est celle du premier [global.json](global-json.md) qui contient le membre `version`. En l’absence de ce membre, la valeur par défaut de `-Version` est `latest`.

`--install-dir <DIRECTORY>`

Spécifie le chemin d’accès de l’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est `$HOME/.dotnet`.

`--architecture <ARCHITECTURE>`

Architecture des fichiers binaires .NET Core à installer. Les valeurs possibles sont `auto`, `x64` et `amd64`. La valeur par défaut est `auto`, qui représente l’architecture de système d’exploitation en cours d’exécution.

`--shared-runtime`

S’il est défini, ce commutateur limite l’installation au runtime partagé. La totalité du SDK n’est pas installée.

`--debug-symbols`

Si cette option est définie, le programme d’installation inclut les symboles de débogage dans l’installation.

> [!NOTE]
> Ce commutateur n’est pas actuellement disponible, mais cela est prévu dans une prochaine version.

`--dry-run`

Si cette option est définie, le script n’effectue pas l’installation, mais affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée. Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération. Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.

`--no-path`

Si cette option est définie, le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle. Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.

`--verbose`

Affiche les informations de diagnostic.

`--azure-feed`

Spécifie l’URL du flux Azure à utiliser par ce programme d’installation. Il n’est pas recommandé de modifier cette valeur. La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.

`--help`

Affiche l’aide pour le script.

## <a name="examples"></a>Exemples

Installez la dernière version de développement à l’emplacement par défaut :

Windows :

`./dotnet-install.ps1 -Channel Future`

Mac OS/Linux :

`./dotnet-install.sh --channel Future`

Installez la dernière préversion à l’emplacement spécifié :

Windows :

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

Mac OS/Linux :

`./dotnet-install.sh --channel preview --install-dir ~/cli`

## <a name="see-also"></a>Voir aussi

[Versions de .NET Core](https://github.com/dotnet/core/releases)   
[Archive de téléchargement de .NET Core Runtime et du Kit SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

