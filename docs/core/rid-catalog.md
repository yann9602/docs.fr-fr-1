---
title: "Catalogue d’identificateurs de runtime (RID) .NET Core"
description: "Découvrez plus en détails l’identificateur de runtime (RID) et la façon dont les identificateurs RID sont utilisés dans .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 180aac7635746f9ede146c3e561deb9bba9a61ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-rid-catalog"></a>Catalogue RID .NET Core

RID est l’abréviation de *Runtime IDentifier* (identificateur de runtime). Les valeurs RID sont utilisées pour identifier les plateformes cibles où l’application s’exécute.
Elles sont utilisées par les packages .NET pour représenter des ressources spécifiques à une plateforme dans les packages NuGet. Les valeurs suivantes sont des exemples d’identificateurs RID : `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.
Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés.

Les RID peuvent être définis dans l’élément `<RuntimeIdentifier>` de votre fichier projet. Ils sont également utilisés par le biais de l’option `--runtime` avec les [commandes de l’interface CLI .NET Core](./tools/index.md) suivantes :

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[architecture]-[additional qualifiers]` où :

- `[os]` représente le moniker du système d’exploitation/de la plateforme. Par exemple, `ubuntu`.

- `[version]` représente la version du système d’exploitation sous la forme d’un numéro de version (`.`) séparé par un point. Par exemple, `15.10`.

  - La version **ne doit pas** correspondre à des versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.

- `[architecture]` représente l’architecture de processeur. Par exemple : `x86`, `x64`, `arm` ou `arm64`.

- `[additional qualifiers]` permet de distinguer davantage les plateformes. Par exemple : `aot` ou `corert`.

## <a name="rid-graph"></a>Graphe RID

Le graphe RID ou le graphe de secours du runtime consiste en une liste d’identificateurs RID compatibles entre eux. Les RID sont définis dans le package [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/). Vous pouvez consulter la liste des RID pris en charge et le graphe RID dans le fichier [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json), situé dans le référentiel CoreFX. Dans ce fichier, vous pouvez voir que tous les RID, sauf celui de base, contiennent une instruction `"#import"`. Ces instructions indiquent des RID compatibles.

Lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour le runtime spécifié.
Si aucune correspondance exacte n’est trouvée, NuGet remonte le graphe jusqu'à ce qu’il trouve le système compatible le plus proche selon le graphe RID.

L’exemple suivant est l’entrée réelle pour le RID `osx.10.12-x64` :

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Le RID ci-dessus indique que `osx.10.12-x64` importe `osx.10.11-x64`. Donc, lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour `osx.10.12-x64` dans le package. Si NuGet ne trouve pas le runtime spécifique, il peut restaurer des packages qui spécifient des runtimes `osx.10.11-x64`, par exemple.

L’exemple suivant illustre un graphe RID légèrement plus grand également défini dans le fichier *runtime.json* :

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Tous les RID sont finalement remappés au RID `any` racine.

Lorsque vous utilisez les RID, il existe quelques remarques que vous devez garder à l’esprit :

- Les RID sont des **chaînes opaques** qui doivent être considérées comme des boîtes noires.
- Ne générez pas les RID par programme.
- Utilisez des RID déjà définis pour la plateforme.
- Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle.

## <a name="using-rids"></a>Utilisation de RID

Pour utiliser des RID, vous devez savoir lesquels existent. De nouvelles valeurs sont régulièrement ajoutées à la plateforme.
Pour en connaître la version complète la plus récente, consultez le fichier [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) dans le référentiel CoreFX.

Le kit SDK .NET Core 2.0 introduit le concept d’identificateurs RID portables. Il s’agit de nouvelles valeurs ajoutées au graphe RID qui ne sont liées à aucune version ou distribution du système d’exploitation spécifique. Elles sont particulièrement utiles lors du traitement de plusieurs distributions Linux.

La liste suivante présente les RID les plus courants utilisés pour chaque système d’exploitation. Elle ne traite pas les valeurs `arm` ou `corert`.

## <a name="windows-rids"></a>RID Windows

- Portable
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 / Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Windows](windows-prerequisites.md).

## <a name="linux-rids"></a>RID Linux

- Portable
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64` (.NET Core 2.0 ou versions ultérieures)
  - `fedora.26-x64` (.NET Core 2.0 ou versions ultérieures)
- Gentoo (.NET Core 2.0 ou versions ultérieures)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET Core 2.0 ou versions ultérieures)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET Core 2.0 ou versions ultérieures)
  - `rhel.7.4-x64` (.NET Core 2.0 ou versions ultérieures)
- Tizen (.NET Core 2.0 ou versions ultérieures)
  - `tizen`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Dérivés d’Ubuntu
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64` (.NET Core 2.0 ou versions ultérieures)

Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Linux](linux-prerequisites.md).

## <a name="macos-rids"></a>RID macOS

Les RID macOS utilisent l’ancien logo « OSX ».

- `osx-x64` (.NET Core 2.0 ou versions ultérieures, la version minimale est `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET Core 1.1 ou versions ultérieures)
- `osx.10.13-x64`

Pour plus d’informations, consultez [Configuration requise pour .NET Core sur macOS](macos-prerequisites.md).

## <a name="android-rids-net-core-20-or-later-versions"></a>RID Android (.NET Core 2.0 ou versions ultérieures)

- `android`
- `android.21`

## <a name="see-also"></a>Voir aussi

[ID du runtime](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
