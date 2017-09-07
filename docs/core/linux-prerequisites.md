---
title: "Prérequis pour .NET Core sur Linux"
description: "Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: johalex
ms.author: johalex
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: c30888895275ce18628ea341fee2d5a77080b8f6
ms.openlocfilehash: ff2b85372208e76c6c3becb551c41cdfb275d272
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a>Prérequis pour .NET Core sur Linux

Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux. Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :

* [Ligne de commande](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Versions de Linux prises en charge

.NET Core 2.x est pris en charge sur les distributions/versions Linux suivantes :

 * Red Hat Enterprise Linux 7 x64
 * CentOS 7 x64
 * Oracle Linux 7 x64
 * Fedora 25, 26 x64
 * Debian 9, 8.7+ x64 
 * Ubuntu 17.04, 16.04, 14.04  x64
 * Linux Mint 18, 17 x64
 * openSUSE 42.2+ x64
 * SUSE Enterprise Linux (SLES) 12 SP2+ x64

.NET Core 1.x est pris en charge sur les distributions/versions Linux suivantes :

* Red Hat Enterprise Linux / CentOS / Oracle Linux 7 x64
* Fedora 24 x64
* Debian 8.2+ x64
* Ubuntu / Linux Mint 14.04, 16.04, 16.10*, 17 x64
* openSUSE 42.1 (1.1) x64
> [!NOTE]
> Ubuntu / Linux 16.10 est pris en charge par la dernière version Release de correctif logiciel de .NET Core 1.1

Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.
## <a name="linux-distribution-dependencies"></a>Dépendances des distributions Linux
### <a name="ubuntu"></a>Ubuntu
Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :

* libunwind8
* libunwind8-dev
* gettext
* libicu-dev
* liblttng-ust-dev
* libcurl4-openssl-dev
* libssl-dev
* uuid-dev
* unzip

### <a name="centos"></a>CentOS
Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :
* deltarpm
* epel-release
* unzip
* libunwind
* gettext
* libcurl-devel
* openssl-devel
* zlib
* libicu-devel

## <a name="installing-net-core-prerequisites-with-the-native-installers"></a>Installation des prérequis pour.NET Core avec les programmes d’installation natifs

Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge. Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur. L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées. En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.

Sur Linux, il existe deux choix pour le package de programme d’installation : 
* Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.
* Utilisation des packages eux-mêmes, DEB ou RPM 

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Script d’installation avec le script de programme d’installation de .NET Core 

Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé. Vous pouvez télécharger les scripts à partir du [référentiel GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain). 

Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives. Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.

> [!IMPORTANT]
> Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Installer .NET Core pour Red Hat Enterprise Linux (RHEL) 7

Pour installer .NET Core sur RHEL 7 :

1. Activez le canal Red Hat .NET, disponible dans votre abonnement RHEL 7.
    * Pour Red Hat Enterprise Server 7, utilisez :
         ```bash
        subscription-manager repos --enable=rhel-7-server-dotnet-rpms
        ```
    * Pour Red Hat Enterprise 7 Workstation, utilisez :
         ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
        ```
    * Pour Red Hat Enterprise 7 HPC Compute Node, utilisez :
         ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. Installez l’outil scl.
    ```bash
    yum install scl-utils
    ```
3. Installer .NET Core
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Installez le runtime et le kit SDK .NET Core 2.0 :
```bash
yum install rh-dotnet20
```
Activez le runtime/kit SDK .NET Core 2.0 pour votre environnement :
```bash
scl enable rh-dotnet20 bash
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

Installez le runtime et le kit SDK .NET Core 1.1 :
```bash
yum install rh-dotnetcore11
```
Activez le runtime et le kit SDK .NET Core 1.1 pour votre environnement :
```bash
scl enable rh-dotnetcore11 bash
```

**.NET Core 1.0**

Installez le runtime et le kit SDK .NET Core 1.0 :
```bash
yum install rh-dotnetcore10
```
Activez le runtime et le kit SDK .NET Core 1.0 pour votre environnement :
```bash
scl enable rh-dotnetcore10 bash
```
---
4. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

     ```bash
     dotnet --help
     ```
> [!NOTE]
> Pour obtenir de l’aide sur l’inscription à l’accès au canal Red Hat .NET, consultez le [chapitre 1 du guide de prise en main de .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) sur Red Hat.


## <a name="install-net-core-for-ubuntu-1404-1604-1610--linux-mint-17-18-64-bit"></a>Installer .NET Core pour Ubuntu 14.04, 16.04, 16.10 & Linux Mint 17, 18 (64 bits)

> [!Warning]
> Avant de commencer, supprimez du système toute version antérieure de .NET Core.

### <a name="add-the-dotnet-apt-get-feed"></a>Ajouter le flux apt-get dotnet

1. Configurez le flux de package hôte de version souhaité.

   **Ubuntu 14.04 / Linux Mint 17**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.04 / Linux Mint 18**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.10**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
2. Installez .NET Core.
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Une fois configuré le flux de package hôte, installez .NET Core 2.0 sur Ubuntu ou Linux Mint :
```bash
sudo apt-get install dotnet-sdk-2.0.0
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Une fois configuré le flux de package hôte, installez .NET Core 1.x sur Ubuntu ou Linux Mint :
```bash
sudo apt-get install dotnet-dev-1.0.4
```
---
3. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

 ```bash
     dotnet --help
 ```
## <a name="install-net-core-for-debian-8-or-9-64-bit"></a>Installer .NET Core pour Debian 8 ou 9 (64 bits)

> [!Warning]
> Avant de commencer, supprimez du système toute version antérieure de .NET Core.

Pour installez .NET Core sur Debian 8 ou 9 (64 bits) :
1. Vérifier les prérequis. 
    ```bash
    sudo apt-get install curl libunwind8 gettext
    ```
2. Téléchargez les fichiers binaires du SDK .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)   

```bash
     curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)   

```bash
     curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
```
---
3. Extrayez les fichiers binaires du SDK .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Ajoutez dotnet au chemin.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

     ```bash
     dotnet --help
     ```

## <a name="install-net-core-for-fedora-24-25-or-26-64-bit"></a>Installer .NET Core pour Fedora 24, 25 ou 26 (64 bits)

> [!Warning]
> Avant de commencer, supprimez du système toute version antérieure de .NET Core.

Pour installer .NET Core pour Fedora 26, 25 (.NET Core 2.x) ou 24 (.NET Core 1.x) : 
1. Vérifier les prérequis. 
    ```bash
    sudo dnf install libunwind libicu
    ```
2. Téléchargez le fichier binaire du SDK .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 ou 25**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
```

---
3. Extrayez les fichiers binaires du SDK .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Ajoutez dotnet au chemin.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>Installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits)

> [!Warning]
> Avant de commencer, supprimez du système toute version antérieure de .NET Core.

Pour installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits) :

1. Vérifier les prérequis.
    ```bash
    sudo dnf install libunwind libicu
    ```
2. Téléchargez le fichier binaire du SDK .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
```

---
3. Extrayez les fichiers binaires du SDK .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Ajoutez dotnet au chemin.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit-net-core-2x-and-opensuse-64-bit"></a>Installer .NET Core pour SUSE Linux Enterprise Server (64 bits) (.NET Core 2.x) et openSUSE (64 bits)

> [!Warning]
> Avant de commencer, supprimez du système toute version antérieure de .NET Core.

Pour Installer .NET Core pour SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits) et openSUSE 42.2 sur NET Core 2.x, ou openSUSE 42.1 (64 bits) sur .NET Core 1.x :

1. Vérifier les prérequis.
    ```bash
    sudo zypper install libunwind libicu
    ```
2. Téléchargez le fichier binaire du SDK .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**SLES 12 SP2, openSUSE 42.2**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**openSUSE 42.1**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
```

---
3. Extrayez les fichiers binaires du SDK .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Ajoutez dotnet au chemin.
    ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.

     ```bash
     dotnet --help
     ```

> [!IMPORTANT]
> En cas de problème avec l’installation de .NET Core 2.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0).
> [!IMPORTANT]
> En cas de problème avec l’installation de .NET Core 1.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ou des [problèmes connus avec la version 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).
