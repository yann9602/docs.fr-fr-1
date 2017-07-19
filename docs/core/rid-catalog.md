---
title: "Catalogue d’identificateurs de runtime (RID) .NET Core | Microsoft Docs"
description: "Catalogue d’identificateurs de runtime (RID) .NET Core"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 904b9be05cd2e5337272ce7ddce15b1075fbefeb
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

<a id="net-core-runtime-identifier-rid-catalog" class="xliff"></a>

# Catalogue d’identificateurs de runtime (RID) .NET Core

<a id="what-are-rids" class="xliff"></a>

## En quoi consistent les RID ?
RID est l’abréviation de *Runtime IDentifier* (identificateur de runtime). Les RID servent à identifier les systèmes d’exploitation cibles sur lesquels une application ou une ressource (c’est-à-dire, un assembly) est appelée à s’exécuter. Il se présentent de la façon suivante : « ubuntu.14.04-x64 », « win7-x64 », « osx.10.11-x64 ». Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés. 

Il est important de noter que les RID sont des chaînes absolument opaques. Cela signifie qu’ils doivent correspondre exactement pour les opérations qui en ont besoin pour fonctionner. Par exemple, prenons le cas d’[Elementary OS](https://elementary.io/), qui est un clone simple d’Ubuntu 14.04. Même si .NET Core et l’interface CLI fonctionnent par-dessus cette version d’Ubuntu, si vous essayez de les utiliser sur Elementary OS sans aucune modification, l’opération de restauration échoue pour n’importe quel package. Cela est dû au fait qu’il n’existe pas actuellement de RID pour désigner Elementary OS en tant que plateforme. 

Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[arch]` où :
- `[os]` représente le moniker du système d’exploitation, par exemple, `ubuntu`.
- `[version]` représente le numéro de version du système d’exploitation séparé par un point (`.`), par exemple, `15.10`, suffisamment précis pour permettre raisonnablement aux ressources de cibler les API de la plateforme du système d’exploitation que cette version représente.
  - Il **ne doit pas** s’agir de versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.
- `[arch]` représente l’architecture du processeur, par exemple, `x86`, `x64`, `arm`, `arm64`, etc.

Le graphique RID est défini dans un package appelé `Microsoft.NETCore.Platforms` dans un fichier appelé `runtime.json`, que vous pouvez trouver dans le [dépôt CoreFX](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json). Si vous utilisez ce fichier, vous remarquerez que certains RID contiennent une instruction `"#import"`. Il s’agit d’une instruction de compatibilité. Autrement dit, un RID qui contient un RID importé peut être une cible pour la restauration de packages pour ce RID. Un peu déroutant, mais appuyons-nous sur un exemple (macOS) pour mieux comprendre :

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
Le RID ci-dessus indique que `osx.10.11-x64` importe `osx.10.10-x64`. Cela signifie qu’à l’occasion d’une restauration de packages, NuGet peut restaurer les packages qui indiquent avoir besoin de `osx.10.10-x64` sur `osx.10.11-x64`.

Voici un exemple de graphique RID légèrement plus complet :  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

Tous les RID sont finalement remappés au RID `any` racine.

Même si leur utilisation paraît assez simple, les RID ont certaines caractéristiques particulières dont vous devez vous rappeler quand vous en utilisez :

* Ce sont des **chaînes opaques** qui doivent être considérées comme des boîtes noires.
    * Vous ne devez pas construire de RID par programmation.
* Vous devez utiliser les RID qui sont déjà définis pour la plateforme, ce qui est illustré dans ce document.
* Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle. Consultez ce document pour identifier le ou les RID dont vous avez besoin pour une plateforme donnée.

<a id="using-rids" class="xliff"></a>

## Utilisation de RID
Pour utiliser des RID, vous devez savoir à quoi ils correspondent. De nouveaux RID sont régulièrement ajoutés à la plateforme. Pour en connaître la version la plus récente, consultez le fichier [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) dans le dépôt CoreFX.

> [!NOTE]
> Nous œuvrons actuellement pour rendre ces informations plus interactives. Cette page sera alors mise à jour et pointera vers cet outil et/ou sa documentation. 

<a id="windows-rids" class="xliff"></a>

## RID Windows

* Windows 7 / Windows Server 2008 R2
    * `win7-x64`
    * `win7-x86`
* Windows 8 / Windows Server 2012
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* Windows 8.1 / Windows Server 2012 R2
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* Windows 10 / Windows Server 2016
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

<a id="linux-rids" class="xliff"></a>

## RID Linux

* Red Hat Enterprise Linux
    * `rhel.7-x64`
* Ubuntu
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* CentOS
    * `centos.7-x64`
* Debian
    * `debian.8-x64`
* Fedora
    * `fedora.23-x64`
    * `fedora.24-x64`
* OpenSUSE
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* Oracle Linux
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* Dérivés d’Ubuntu actuellement pris en charge 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

<a id="os-x-rids" class="xliff"></a>

## RID OS X

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

