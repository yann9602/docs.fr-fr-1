---
title: Scripts dotnet-install | SDK .NET Core
description: "En savoir plus sur les scripts dotnet-install pour installer les outils CLI .NET Core et le runtime partagé."
keywords: dotnet-install, scripts dotnet-install, .NET Core
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 59b9c456-2bfd-4adc-8202-a1c6a0a6c787
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 30e969c55d08b3ac276c6e7786fa96985dbb0a6b

---

#<a name="dotnetinstall-scripts-reference"></a>Documentation sur les scripts dotnet-install

## <a name="name"></a>Nom
dotnet-install.ps1 | dotnet-install.sh - script utilisé pour installer les outils de l’interface de ligne de commande (CLI) et le runtime partagé

## <a name="synopsis"></a>Résumé
Windows :

`dotnet-install.ps1 [-Channel] [-Version]
    [-InstallDir] [-Debug] [-NoPath] 
    [-SharedRuntime]`

Mac OS/Linux :

`dotnet-install.sh [--channel] [--version]
    [--install-dir] [--debug] [--no-path] 
    [--shared-runtime]`

## <a name="description"></a>Description
Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé. Vous pouvez télécharger les scripts à partir de notre [dépôt GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain). 

Ils sont principalement utilisés pour faciliter l’automatisation et les installations non administrateur. Il existe deux scripts : un script PowerShell qui fonctionne avec Windows, et un script d’interpréteur de commandes qui fonctionne avec Linux/OS X. Ces deux scripts ont le même comportement. Le script d’interpréteur de commandes accepte également les commutateurs PowerShell. Vous pouvez donc les utiliser partout. 

Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `--install-dir`. Par défaut, le script d’installation télécharge le SDK et l’installe. Si vous souhaitez seulement obtenir le runtime partagé, vous pouvez spécifier l’argument `--shared-runtime`. 

Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active. Il peut être remplacé si l’argument `--no-path` est utilisé. 

Avant d’exécuter le script, installez toutes les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.

Vous pouvez installer une version spécifique à l’aide de l’argument `--version`. La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232). Si vous ne spécifiez pas de version, la valeur utilisée par défaut sera celle du premier fichier [global.json](global-json.md) trouvé dans la hiérarchie au-dessus du dossier dans lequel le script a été appelé, et qui contient la propriété `version`. Si cette propriété est absente, la propriété « Latest » est utilisée.

Vous pouvez également utiliser ce script pour obtenir le SDK ou les fichiers binaires de débogage de runtime partagé avec les symboles de débogage, à l’aide de l’argument `--debug`. Si vous ne faites pas cela lors de la première installation et si vous vous rendez compte plus tard que vous avez besoin de symboles de débogage, vous pouvez réexécuter le script avec cet argument et la version de bits que vous avez installée. 

## <a name="options"></a>Options
Les options diffèrent d’une implémentation de script à l’autre. 

### <a name="powershell-windows"></a>PowerShell (Windows)
`-Channel [CHANNEL]`

Le canal (par exemple, `future`, `preview`, `production`) à partir duquel effectuer l’installation. La valeur par défaut est `production`.

`-Version [VERSION]`

Version de l’interface CLI à installer. Vous devez spécifier la version en trois parties (par exemple, 1.0.0-13232). Si vous ne spécifiez pas de version, la valeur utilisée par défaut sera celle du premier fichier [global.json](global-json.md) qui contient la propriété `version`. Si cette propriété est absente, la propriété Latest est utilisée.     

`-InstallDir [DIR]`

Chemin d’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est *% LocalAppData%\.dotnet*.

`-Debug`

`true` pour indiquer que les packages volumineux contenant des symboles de débogage doivent être utilisés ; sinon, `false`. La valeur par défaut est `false`.

`-NoPath`

`true` pour indiquer que le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle ; sinon, `false`. La valeur par défaut est `false`, c’est-à-dire que PATH est modifié. Les outils CLI sont ainsi disponibles immédiatement après l’installation. 

`-SharedRuntime`

`true` pour installer uniquement les bits du runtime partagé ; `false` pour installer le SDK dans son intégralité. La valeur par défaut est `false`.

### <a name="bash-macoslinux"></a>Interpréteur de commandes (Mac OS/Linux)
`--channel [CHANNEL]`

Le canal (par exemple « future », « preview », « production ») à partir duquel effectuer l’installation. La valeur par défaut est « Production ».

`--version [VERSION]`

Version de l’interface CLI à installer. Vous devez spécifier la version en trois parties (par exemple, 1.0.0-13232). Si vous ne spécifiez pas de version, la valeur utilisée par défaut sera celle du premier fichier [global.json](global-json.md) qui contient la propriété `version`. Si cette propriété est absente, la propriété Latest est utilisée.     

`--install-dir [DIR]`

Chemin d’installation. S’il n’existe pas déjà, le répertoire est créé. La valeur par défaut est `$HOME/.dotnet`.

`--debug`

`true` pour indiquer que les packages volumineux contenant des symboles de débogage doivent être utilisés ; sinon, `false`. La valeur par défaut est `false`.

`--no-path`

`true` pour indiquer que le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle ; sinon, `false`. La valeur par défaut est `false`, c’est-à-dire que PATH est modifié. Les outils CLI sont ainsi disponibles immédiatement après l’installation.  

`--shared-runtime`

`true` pour installer uniquement les bits du runtime partagé ; `false` pour installer le SDK dans son intégralité. La valeur par défaut est `false`.

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



<!--HONumber=Nov16_HO1-->


