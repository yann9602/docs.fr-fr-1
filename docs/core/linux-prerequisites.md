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

# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="dfb71-104">Prérequis pour .NET Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="dfb71-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="dfb71-105">Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux.</span><span class="sxs-lookup"><span data-stu-id="dfb71-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="dfb71-106">Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :</span><span class="sxs-lookup"><span data-stu-id="dfb71-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="dfb71-107">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="dfb71-107">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="dfb71-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dfb71-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="dfb71-109">Versions de Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="dfb71-109">Supported Linux versions</span></span>

<span data-ttu-id="dfb71-110">.NET Core 2.x est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfb71-110">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

 * <span data-ttu-id="dfb71-111">Red Hat Enterprise Linux 7 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-111">Red Hat Enterprise Linux 7 x64</span></span>
 * <span data-ttu-id="dfb71-112">CentOS 7 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-112">CentOS 7 x64</span></span>
 * <span data-ttu-id="dfb71-113">Oracle Linux 7 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-113">Oracle Linux 7 x64</span></span>
 * <span data-ttu-id="dfb71-114">Fedora 25, 26 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-114">Fedora 25, 26 x64</span></span>
 * <span data-ttu-id="dfb71-115">Debian 9, 8.7+ x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-115">Debian 9, 8.7+ x64</span></span> 
 * <span data-ttu-id="dfb71-116">Ubuntu 17.04, 16.04, 14.04  x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-116">Ubuntu 17.04, 16.04, 14.04  x64</span></span>
 * <span data-ttu-id="dfb71-117">Linux Mint 18, 17 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-117">Linux Mint 18, 17 x64</span></span>
 * <span data-ttu-id="dfb71-118">openSUSE 42.2+ x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-118">openSUSE 42.2+ x64</span></span>
 * <span data-ttu-id="dfb71-119">SUSE Enterprise Linux (SLES) 12 SP2+ x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-119">SUSE Enterprise Linux (SLES) 12 SP2+ x64</span></span>

<span data-ttu-id="dfb71-120">.NET Core 1.x est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfb71-120">.NET Core 1.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="dfb71-121">Red Hat Enterprise Linux / CentOS / Oracle Linux 7 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-121">Red Hat Enterprise Linux / CentOS / Oracle Linux 7 x64</span></span>
* <span data-ttu-id="dfb71-122">Fedora 24 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-122">Fedora 24 x64</span></span>
* <span data-ttu-id="dfb71-123">Debian 8.2+ x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-123">Debian 8.2+ x64</span></span>
* <span data-ttu-id="dfb71-124">Ubuntu / Linux Mint 14.04, 16.04, 16.10*, 17 x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-124">Ubuntu / Linux Mint 14.04, 16.04, 16.10*, 17 x64</span></span>
* <span data-ttu-id="dfb71-125">openSUSE 42.1 (1.1) x64</span><span class="sxs-lookup"><span data-stu-id="dfb71-125">openSUSE 42.1 (1.1) x64</span></span>
> [!NOTE]
> <span data-ttu-id="dfb71-126">Ubuntu / Linux 16.10 est pris en charge par la dernière version Release de correctif logiciel de .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="dfb71-126">Ubuntu / Linux 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>

<span data-ttu-id="dfb71-127">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="dfb71-127">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="dfb71-128">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="dfb71-128">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>
## <a name="linux-distribution-dependencies"></a><span data-ttu-id="dfb71-129">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="dfb71-129">Linux Distribution Dependencies</span></span>
### <a name="ubuntu"></a><span data-ttu-id="dfb71-130">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="dfb71-130">Ubuntu</span></span>
<span data-ttu-id="dfb71-131">Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfb71-131">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="dfb71-132">libunwind8</span><span class="sxs-lookup"><span data-stu-id="dfb71-132">libunwind8</span></span>
* <span data-ttu-id="dfb71-133">libunwind8-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-133">libunwind8-dev</span></span>
* <span data-ttu-id="dfb71-134">gettext</span><span class="sxs-lookup"><span data-stu-id="dfb71-134">gettext</span></span>
* <span data-ttu-id="dfb71-135">libicu-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-135">libicu-dev</span></span>
* <span data-ttu-id="dfb71-136">liblttng-ust-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-136">liblttng-ust-dev</span></span>
* <span data-ttu-id="dfb71-137">libcurl4-openssl-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-137">libcurl4-openssl-dev</span></span>
* <span data-ttu-id="dfb71-138">libssl-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-138">libssl-dev</span></span>
* <span data-ttu-id="dfb71-139">uuid-dev</span><span class="sxs-lookup"><span data-stu-id="dfb71-139">uuid-dev</span></span>
* <span data-ttu-id="dfb71-140">unzip</span><span class="sxs-lookup"><span data-stu-id="dfb71-140">unzip</span></span>

### <a name="centos"></a><span data-ttu-id="dfb71-141">CentOS</span><span class="sxs-lookup"><span data-stu-id="dfb71-141">CentOS</span></span>
<span data-ttu-id="dfb71-142">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfb71-142">CentOS distributions require the following libraries installed:</span></span>
* <span data-ttu-id="dfb71-143">deltarpm</span><span class="sxs-lookup"><span data-stu-id="dfb71-143">deltarpm</span></span>
* <span data-ttu-id="dfb71-144">epel-release</span><span class="sxs-lookup"><span data-stu-id="dfb71-144">epel-release</span></span>
* <span data-ttu-id="dfb71-145">unzip</span><span class="sxs-lookup"><span data-stu-id="dfb71-145">unzip</span></span>
* <span data-ttu-id="dfb71-146">libunwind</span><span class="sxs-lookup"><span data-stu-id="dfb71-146">libunwind</span></span>
* <span data-ttu-id="dfb71-147">gettext</span><span class="sxs-lookup"><span data-stu-id="dfb71-147">gettext</span></span>
* <span data-ttu-id="dfb71-148">libcurl-devel</span><span class="sxs-lookup"><span data-stu-id="dfb71-148">libcurl-devel</span></span>
* <span data-ttu-id="dfb71-149">openssl-devel</span><span class="sxs-lookup"><span data-stu-id="dfb71-149">openssl-devel</span></span>
* <span data-ttu-id="dfb71-150">zlib</span><span class="sxs-lookup"><span data-stu-id="dfb71-150">zlib</span></span>
* <span data-ttu-id="dfb71-151">libicu-devel</span><span class="sxs-lookup"><span data-stu-id="dfb71-151">libicu-devel</span></span>

## <a name="installing-net-core-prerequisites-with-the-native-installers"></a><span data-ttu-id="dfb71-152">Installation des prérequis pour.NET Core avec les programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="dfb71-152">Installing .NET Core Prerequisites With the Native Installers</span></span>

<span data-ttu-id="dfb71-153">Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="dfb71-153">.NET Core native installers are available for supported Linux distributions/ versions.</span></span> <span data-ttu-id="dfb71-154">Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur.</span><span class="sxs-lookup"><span data-stu-id="dfb71-154">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="dfb71-155">L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées.</span><span class="sxs-lookup"><span data-stu-id="dfb71-155">The advantage of using a native installer is that the all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="dfb71-156">En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="dfb71-156">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="dfb71-157">Sur Linux, il existe deux choix pour le package de programme d’installation :</span><span class="sxs-lookup"><span data-stu-id="dfb71-157">On Linux, there are two installer package choices:</span></span> 
* <span data-ttu-id="dfb71-158">Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="dfb71-158">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="dfb71-159">Utilisation des packages eux-mêmes, DEB ou RPM</span><span class="sxs-lookup"><span data-stu-id="dfb71-159">Using the packages themselves, DEB or RPM.</span></span> 

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="dfb71-160">Script d’installation avec le script de programme d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="dfb71-160">Scripting Installs With the .NET Core Installer Script</span></span> 

<span data-ttu-id="dfb71-161">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="dfb71-161">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="dfb71-162">Vous pouvez télécharger les scripts à partir du [référentiel GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span><span class="sxs-lookup"><span data-stu-id="dfb71-162">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span> 

<span data-ttu-id="dfb71-163">Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives.</span><span class="sxs-lookup"><span data-stu-id="dfb71-163">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="dfb71-164">Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="dfb71-164">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfb71-165">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="dfb71-165">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dfb71-166">Installer .NET Core pour Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dfb71-166">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dfb71-167">Pour installer .NET Core sur RHEL 7 :</span><span class="sxs-lookup"><span data-stu-id="dfb71-167">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="dfb71-168">Activez le canal Red Hat .NET, disponible dans votre abonnement RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="dfb71-168">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="dfb71-169">Pour Red Hat Enterprise Server 7, utilisez :</span><span class="sxs-lookup"><span data-stu-id="dfb71-169">For Red Hat Enterprise 7 Server, use:</span></span>
         ```bash
        subscription-manager repos --enable=rhel-7-server-dotnet-rpms
        ```
    * <span data-ttu-id="dfb71-170">Pour Red Hat Enterprise 7 Workstation, utilisez :</span><span class="sxs-lookup"><span data-stu-id="dfb71-170">For Red Hat Enterprise 7 Workstation, use:</span></span>
         ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
        ```
    * <span data-ttu-id="dfb71-171">Pour Red Hat Enterprise 7 HPC Compute Node, utilisez :</span><span class="sxs-lookup"><span data-stu-id="dfb71-171">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
         ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="dfb71-172">Installez l’outil scl.</span><span class="sxs-lookup"><span data-stu-id="dfb71-172">Install the scl tool.</span></span>
    ```bash
    yum install scl-utils
    ```
3. <span data-ttu-id="dfb71-173">Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="dfb71-173">Install .NET Core</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-174">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-174">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="dfb71-175">Installez le runtime et le kit SDK .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="dfb71-175">Install .NET Core 2.0 SDK and Runtime:</span></span>
```bash
yum install rh-dotnet20
```
<span data-ttu-id="dfb71-176">Activez le runtime/kit SDK .NET Core 2.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="dfb71-176">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>
```bash
scl enable rh-dotnet20 bash
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-177">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dfb71-178">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="dfb71-178">**.NET Core 1.1**</span></span>

<span data-ttu-id="dfb71-179">Installez le runtime et le kit SDK .NET Core 1.1 :</span><span class="sxs-lookup"><span data-stu-id="dfb71-179">Install .NET Core 1.1 SDK and Runtime:</span></span>
```bash
yum install rh-dotnetcore11
```
<span data-ttu-id="dfb71-180">Activez le runtime et le kit SDK .NET Core 1.1 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="dfb71-180">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>
```bash
scl enable rh-dotnetcore11 bash
```

<span data-ttu-id="dfb71-181">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="dfb71-181">**.NET Core 1.0**</span></span>

<span data-ttu-id="dfb71-182">Installez le runtime et le kit SDK .NET Core 1.0 :</span><span class="sxs-lookup"><span data-stu-id="dfb71-182">Install .NET Core 1.0 SDK and Runtime:</span></span>
```bash
yum install rh-dotnetcore10
```
<span data-ttu-id="dfb71-183">Activez le runtime et le kit SDK .NET Core 1.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="dfb71-183">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>
```bash
scl enable rh-dotnetcore10 bash
```
---
4. <span data-ttu-id="dfb71-184">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-184">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --help
     ```
> [!NOTE]
> <span data-ttu-id="dfb71-185">Pour obtenir de l’aide sur l’inscription à l’accès au canal Red Hat .NET, consultez le [chapitre 1 du guide de prise en main de .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) sur Red Hat.</span><span class="sxs-lookup"><span data-stu-id="dfb71-185">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>


## <a name="install-net-core-for-ubuntu-1404-1604-1610--linux-mint-17-18-64-bit"></a><span data-ttu-id="dfb71-186">Installer .NET Core pour Ubuntu 14.04, 16.04, 16.10 & Linux Mint 17, 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="dfb71-186">Install .NET Core for Ubuntu 14.04, 16.04, 16.10 & Linux Mint 17, 18 (64 bit)</span></span>

> [!Warning]
> <span data-ttu-id="dfb71-187">Avant de commencer, supprimez du système toute version antérieure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-187">Before you start, remove any previous versions of .NET Core from your system.</span></span>

### <a name="add-the-dotnet-apt-get-feed"></a><span data-ttu-id="dfb71-188">Ajouter le flux apt-get dotnet</span><span class="sxs-lookup"><span data-stu-id="dfb71-188">Add the dotnet apt-get feed</span></span>

1. <span data-ttu-id="dfb71-189">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="dfb71-189">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="dfb71-190">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="dfb71-190">**Ubuntu 14.04 / Linux Mint 17**</span></span>
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    <span data-ttu-id="dfb71-191">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="dfb71-191">**Ubuntu 16.04 / Linux Mint 18**</span></span>
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    <span data-ttu-id="dfb71-192">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="dfb71-192">**Ubuntu 16.10**</span></span>
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
2. <span data-ttu-id="dfb71-193">Installez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-193">Install .NET Core.</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-194">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-194">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="dfb71-195">Une fois configuré le flux de package hôte, installez .NET Core 2.0 sur Ubuntu ou Linux Mint :</span><span class="sxs-lookup"><span data-stu-id="dfb71-195">After host package feed setup, install .NET Core 2.0 on Ubuntu or Linux Mint:</span></span>
```bash
sudo apt-get install dotnet-sdk-2.0.0
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dfb71-197">Une fois configuré le flux de package hôte, installez .NET Core 1.x sur Ubuntu ou Linux Mint :</span><span class="sxs-lookup"><span data-stu-id="dfb71-197">After host package feed setup, install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>
```bash
sudo apt-get install dotnet-dev-1.0.4
```
---
3. <span data-ttu-id="dfb71-198">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-198">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

 ```bash
     dotnet --help
 ```
## <a name="install-net-core-for-debian-8-or-9-64-bit"></a><span data-ttu-id="dfb71-199">Installer .NET Core pour Debian 8 ou 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="dfb71-199">Install .NET Core for Debian 8 or 9 (64 bit).</span></span>

> [!Warning]
> <span data-ttu-id="dfb71-200">Avant de commencer, supprimez du système toute version antérieure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-200">Before you start, remove any previous versions of .NET Core from your system.</span></span>

<span data-ttu-id="dfb71-201">Pour installez .NET Core sur Debian 8 ou 9 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="dfb71-201">To install .NET Core on Debian 8 or 9 (64 bit):</span></span>
1. <span data-ttu-id="dfb71-202">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="dfb71-202">Get the prerequisites.</span></span> 
    ```bash
    sudo apt-get install curl libunwind8 gettext
    ```
2. <span data-ttu-id="dfb71-203">Téléchargez les fichiers binaires du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="dfb71-203">Download the .NET Core SDK binaries (tarball).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-204">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-204">.NET Core 2.x</span></span>](#tab/netcore2x)   

```bash
     curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-205">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-205">.NET Core 1.x</span></span>](#tab/netcore1x)   

```bash
     curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
```
---
3. <span data-ttu-id="dfb71-206">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-206">Extract the .NET Core SDK binaries.</span></span>
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. <span data-ttu-id="dfb71-207">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="dfb71-207">Add dotnet to your PATH.</span></span>
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. <span data-ttu-id="dfb71-208">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-208">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --help
     ```

## <a name="install-net-core-for-fedora-24-25-or-26-64-bit"></a><span data-ttu-id="dfb71-209">Installer .NET Core pour Fedora 24, 25 ou 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="dfb71-209">Install .NET Core for Fedora 24, 25, or 26 (64 bit)</span></span>

> [!Warning]
> <span data-ttu-id="dfb71-210">Avant de commencer, supprimez du système toute version antérieure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-210">Before you start, remove any previous versions of .NET Core from your system.</span></span>

<span data-ttu-id="dfb71-211">Pour installer .NET Core pour Fedora 26, 25 (.NET Core 2.x) ou 24 (.NET Core 1.x) :</span><span class="sxs-lookup"><span data-stu-id="dfb71-211">To Install .NET Core for Fedora 26,25(.NET Core 2.x) or 24 (.NET Core 1.x):</span></span> 
1. <span data-ttu-id="dfb71-212">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="dfb71-212">Get the prerequisites.</span></span> 
    ```bash
    sudo dnf install libunwind libicu
    ```
2. <span data-ttu-id="dfb71-213">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="dfb71-213">Download the .NET Core SDK binary  (tarball).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-214">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-214">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="dfb71-215">**Fedora 26 ou 25**</span><span class="sxs-lookup"><span data-stu-id="dfb71-215">**Fedora 26 or 25**</span></span>

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-216">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-216">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dfb71-217">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="dfb71-217">**Fedora 24**</span></span>

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
```

---
3. <span data-ttu-id="dfb71-218">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-218">Extract the .NET Core SDK binaries.</span></span>
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. <span data-ttu-id="dfb71-219">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="dfb71-219">Add dotnet to your PATH.</span></span>
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. <span data-ttu-id="dfb71-220">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-220">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="dfb71-221">Installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="dfb71-221">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

> [!Warning]
> <span data-ttu-id="dfb71-222">Avant de commencer, supprimez du système toute version antérieure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-222">Before you start, remove any previous versions of .NET Core from your system.</span></span>

<span data-ttu-id="dfb71-223">Pour installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="dfb71-223">To Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="dfb71-224">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="dfb71-224">Get the prerequisites.</span></span>
    ```bash
    sudo dnf install libunwind libicu
    ```
2. <span data-ttu-id="dfb71-225">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="dfb71-225">Download the .NET Core SDK binary (tarball).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-226">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-226">.NET Core 2.x</span></span>](#tab/netcore2x)

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-227">.NET Core 1.x</span></span>](#tab/netcore1x)

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
```

---
3. <span data-ttu-id="dfb71-228">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-228">Extract the .NET Core SDK binaries.</span></span>
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. <span data-ttu-id="dfb71-229">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="dfb71-229">Add dotnet to your PATH.</span></span>
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. <span data-ttu-id="dfb71-230">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-230">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit-net-core-2x-and-opensuse-64-bit"></a><span data-ttu-id="dfb71-231">Installer .NET Core pour SUSE Linux Enterprise Server (64 bits) (.NET Core 2.x) et openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="dfb71-231">Install .NET Core for SUSE Linux Enterprise Server (64 bit) (.NET Core 2.x) and openSUSE (64 bit)</span></span>

> [!Warning]
> <span data-ttu-id="dfb71-232">Avant de commencer, supprimez du système toute version antérieure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-232">Before you start, remove any previous versions of .NET Core from your system.</span></span>

<span data-ttu-id="dfb71-233">Pour Installer .NET Core pour SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits) et openSUSE 42.2 sur NET Core 2.x, ou openSUSE 42.1 (64 bits) sur .NET Core 1.x :</span><span class="sxs-lookup"><span data-stu-id="dfb71-233">To Install .NET Core for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit) and openSUSE 42.2 on NET Core 2.x, or openSUSE 42.1(64 bit) on .NET Core 1.x:</span></span>

1. <span data-ttu-id="dfb71-234">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="dfb71-234">Get the prerequisites.</span></span>
    ```bash
    sudo zypper install libunwind libicu
    ```
2. <span data-ttu-id="dfb71-235">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="dfb71-235">Download the .NET Core SDK binary (tarball).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dfb71-236">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="dfb71-237">**SLES 12 SP2, openSUSE 42.2**</span><span class="sxs-lookup"><span data-stu-id="dfb71-237">**SLES 12 SP2, openSUSE 42.2**</span></span>

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dfb71-238">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="dfb71-238">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="dfb71-239">**openSUSE 42.1**</span><span class="sxs-lookup"><span data-stu-id="dfb71-239">**openSUSE 42.1**</span></span>

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
```

---
3. <span data-ttu-id="dfb71-240">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dfb71-240">Extract the .NET Core SDK binaries.</span></span>
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. <span data-ttu-id="dfb71-241">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="dfb71-241">Add dotnet to your PATH.</span></span>
    ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. <span data-ttu-id="dfb71-242">Exécutez la commande `dotnet --help` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="dfb71-242">Run the `dotnet --help` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --help
     ```

> [!IMPORTANT]
> <span data-ttu-id="dfb71-243">En cas de problème avec l’installation de .NET Core 2.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0).</span><span class="sxs-lookup"><span data-stu-id="dfb71-243">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="dfb71-244">En cas de problème avec l’installation de .NET Core 1.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ou des [problèmes connus avec la version 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="dfb71-244">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
