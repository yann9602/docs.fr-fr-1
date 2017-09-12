---
title: "Prérequis pour .NET Core sur Linux"
description: "Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 7bbb8405f39a52d2798fd1dbc78f3116cb3bedbb
ms.openlocfilehash: 9864ffa31caa007cb649a9e6e8913863d9cb2c35
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="ddfca-104">Prérequis pour .NET Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="ddfca-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="ddfca-105">Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux.</span><span class="sxs-lookup"><span data-stu-id="ddfca-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="ddfca-106">Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :</span><span class="sxs-lookup"><span data-stu-id="ddfca-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="ddfca-107">Ligne de commande avec votre éditeur favori</span><span class="sxs-lookup"><span data-stu-id="ddfca-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="ddfca-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ddfca-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="ddfca-109">Versions de Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="ddfca-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ddfca-111">.NET Core 2.0 traite Linux comme un seul système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ddfca-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="ddfca-112">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ddfca-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="ddfca-113">.NET Core 2.x est pris en charge sur les distributions/versions Linux x64 suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddfca-113">NET Core 2.x is supported on the following Linux x64 distributions/versions:</span></span>

 * <span data-ttu-id="ddfca-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="ddfca-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-115">CentOS 7</span></span>
 * <span data-ttu-id="ddfca-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="ddfca-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="ddfca-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="ddfca-118">Debian 8.7 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ddfca-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="ddfca-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ddfca-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="ddfca-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="ddfca-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="ddfca-121">openSUSE 42.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ddfca-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="ddfca-122">SUSE Enterprise Linux (SLES) 12 SP2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ddfca-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="ddfca-123">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="ddfca-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ddfca-125">.NET Core 1.x est pris en charge sur les distributions/versions Linux x64 suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddfca-125">.NET Core 1.x is supported on the following Linux x64 distributions/versions:</span></span>

* <span data-ttu-id="ddfca-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="ddfca-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-127">CentOS 7</span></span>
* <span data-ttu-id="ddfca-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-128">Oracle Linux 7</span></span>
* <span data-ttu-id="ddfca-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="ddfca-129">Fedora 24</span></span>
* <span data-ttu-id="ddfca-130">Debian 8.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ddfca-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="ddfca-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="ddfca-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="ddfca-132">Ubuntu 16.10 est pris en charge par la dernière version de correctif logiciel de .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="ddfca-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="ddfca-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="ddfca-133">Linux Mint 17</span></span>
* <span data-ttu-id="ddfca-134">openSUSE 42.1 ou versions ultérieures (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="ddfca-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="ddfca-135">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="ddfca-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="ddfca-136">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="ddfca-136">Linux distribution dependencies</span></span>

### <a name="ubuntu"></a><span data-ttu-id="ddfca-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ddfca-137">Ubuntu</span></span>

<span data-ttu-id="ddfca-138">Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddfca-138">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="ddfca-139">libunwind8</span><span class="sxs-lookup"><span data-stu-id="ddfca-139">libunwind8</span></span>
* <span data-ttu-id="ddfca-140">libunwind8-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-140">libunwind8-dev</span></span>
* <span data-ttu-id="ddfca-141">gettext</span><span class="sxs-lookup"><span data-stu-id="ddfca-141">gettext</span></span>
* <span data-ttu-id="ddfca-142">libicu-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-142">libicu-dev</span></span>
* <span data-ttu-id="ddfca-143">liblttng-ust-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-143">liblttng-ust-dev</span></span>
* <span data-ttu-id="ddfca-144">libcurl4-openssl-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-144">libcurl4-openssl-dev</span></span>
* <span data-ttu-id="ddfca-145">libssl-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-145">libssl-dev</span></span>
* <span data-ttu-id="ddfca-146">uuid-dev</span><span class="sxs-lookup"><span data-stu-id="ddfca-146">uuid-dev</span></span>
* <span data-ttu-id="ddfca-147">unzip</span><span class="sxs-lookup"><span data-stu-id="ddfca-147">unzip</span></span>

### <a name="centos"></a><span data-ttu-id="ddfca-148">CentOS</span><span class="sxs-lookup"><span data-stu-id="ddfca-148">CentOS</span></span>

<span data-ttu-id="ddfca-149">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddfca-149">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="ddfca-150">deltarpm</span><span class="sxs-lookup"><span data-stu-id="ddfca-150">deltarpm</span></span>
* <span data-ttu-id="ddfca-151">epel-release</span><span class="sxs-lookup"><span data-stu-id="ddfca-151">epel-release</span></span>
* <span data-ttu-id="ddfca-152">unzip</span><span class="sxs-lookup"><span data-stu-id="ddfca-152">unzip</span></span>
* <span data-ttu-id="ddfca-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="ddfca-153">libunwind</span></span>
* <span data-ttu-id="ddfca-154">gettext</span><span class="sxs-lookup"><span data-stu-id="ddfca-154">gettext</span></span>
* <span data-ttu-id="ddfca-155">libcurl-devel</span><span class="sxs-lookup"><span data-stu-id="ddfca-155">libcurl-devel</span></span>
* <span data-ttu-id="ddfca-156">openssl-devel</span><span class="sxs-lookup"><span data-stu-id="ddfca-156">openssl-devel</span></span>
* <span data-ttu-id="ddfca-157">zlib</span><span class="sxs-lookup"><span data-stu-id="ddfca-157">zlib</span></span>
* <span data-ttu-id="ddfca-158">libicu-devel</span><span class="sxs-lookup"><span data-stu-id="ddfca-158">libicu-devel</span></span>

<span data-ttu-id="ddfca-159">Pour plus d’informations sur les dépendances, consultez [Applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (en anglais).</span><span class="sxs-lookup"><span data-stu-id="ddfca-159">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="ddfca-160">Installation des dépendances .NET Core avec les programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="ddfca-160">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="ddfca-161">Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ddfca-161">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="ddfca-162">Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur.</span><span class="sxs-lookup"><span data-stu-id="ddfca-162">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="ddfca-163">L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées.</span><span class="sxs-lookup"><span data-stu-id="ddfca-163">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="ddfca-164">En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="ddfca-164">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="ddfca-165">Sur Linux, il existe deux choix pour le package de programme d’installation :</span><span class="sxs-lookup"><span data-stu-id="ddfca-165">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="ddfca-166">Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="ddfca-166">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="ddfca-167">Utilisation des packages eux-mêmes, DEB ou RPM</span><span class="sxs-lookup"><span data-stu-id="ddfca-167">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="ddfca-168">Script d’installation avec le script de programme d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddfca-168">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="ddfca-169">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="ddfca-169">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="ddfca-170">Vous pouvez télécharger les scripts à partir du [référentiel GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span><span class="sxs-lookup"><span data-stu-id="ddfca-170">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span>

<span data-ttu-id="ddfca-171">Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives.</span><span class="sxs-lookup"><span data-stu-id="ddfca-171">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="ddfca-172">Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="ddfca-172">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddfca-173">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ddfca-173">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ddfca-174">Installer .NET Core pour Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ddfca-174">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ddfca-175">Pour installer .NET Core sur RHEL 7 :</span><span class="sxs-lookup"><span data-stu-id="ddfca-175">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="ddfca-176">Activez le canal Red Hat .NET, disponible dans votre abonnement RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="ddfca-176">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="ddfca-177">Pour Red Hat Enterprise Server 7, utilisez :</span><span class="sxs-lookup"><span data-stu-id="ddfca-177">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="ddfca-178">Pour Red Hat Enterprise 7 Workstation, utilisez :</span><span class="sxs-lookup"><span data-stu-id="ddfca-178">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="ddfca-179">Pour Red Hat Enterprise 7 HPC Compute Node, utilisez :</span><span class="sxs-lookup"><span data-stu-id="ddfca-179">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="ddfca-180">Installez l’outil scl.</span><span class="sxs-lookup"><span data-stu-id="ddfca-180">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="ddfca-181">Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddfca-181">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-182">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-182">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ddfca-183">Installez le runtime et le kit SDK .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="ddfca-183">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="ddfca-184">Activez le runtime/kit SDK .NET Core 2.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="ddfca-184">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-185">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-185">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ddfca-186">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="ddfca-186">**.NET Core 1.1**</span></span>

<span data-ttu-id="ddfca-187">Installez le runtime et le kit SDK .NET Core 1.1 :</span><span class="sxs-lookup"><span data-stu-id="ddfca-187">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="ddfca-188">Activez le runtime et le kit SDK .NET Core 1.1 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="ddfca-188">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="ddfca-189">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="ddfca-189">**.NET Core 1.0**</span></span>

<span data-ttu-id="ddfca-190">Installez le runtime et le kit SDK .NET Core 1.0 :</span><span class="sxs-lookup"><span data-stu-id="ddfca-190">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="ddfca-191">Activez le runtime et le kit SDK .NET Core 1.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="ddfca-191">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="ddfca-192">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-192">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="ddfca-193">Pour obtenir de l’aide sur l’inscription à l’accès au canal Red Hat .NET, consultez le [chapitre 1 du guide de prise en main de .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) sur Red Hat.</span><span class="sxs-lookup"><span data-stu-id="ddfca-193">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="ddfca-194">Installer .NET Core pour Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10, Linux Mint 17 et Linux Mint 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-194">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="ddfca-195">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-195">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-196">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-196">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="ddfca-197">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="ddfca-197">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="ddfca-198">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="ddfca-198">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="ddfca-199">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="ddfca-199">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="ddfca-200">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="ddfca-200">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="ddfca-201">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="ddfca-201">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="ddfca-202">Installez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-202">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="ddfca-203">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-203">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-204">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-204">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="ddfca-205">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="ddfca-205">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="ddfca-206">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="ddfca-206">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="ddfca-207">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="ddfca-207">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="ddfca-208">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="ddfca-208">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="ddfca-209">Installez .NET Core 1.x sur Ubuntu ou Linux Mint :</span><span class="sxs-lookup"><span data-stu-id="ddfca-209">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="ddfca-210">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-210">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="ddfca-211">Installer .NET Core pour Debian 8 ou Debian 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-211">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="ddfca-212">Pour installer .NET Core sur Debian 8 ou Debian 9 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="ddfca-212">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="ddfca-213">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-213">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="ddfca-214">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="ddfca-214">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-215">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-215">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="ddfca-216">Installez les composants du système.</span><span class="sxs-lookup"><span data-stu-id="ddfca-216">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="ddfca-217">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="ddfca-217">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="ddfca-218">Enregistrez le flux de produit Microsoft approuvé.</span><span class="sxs-lookup"><span data-stu-id="ddfca-218">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="ddfca-219">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="ddfca-219">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="ddfca-220">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="ddfca-220">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="ddfca-221">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-221">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="ddfca-222">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-222">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-223">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-223">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="ddfca-224">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="ddfca-224">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="ddfca-225">Téléchargez les fichiers binaires du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="ddfca-225">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="ddfca-226">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-226">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="ddfca-227">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-227">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="ddfca-228">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-228">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="ddfca-229">Installer .NET Core pour Fedora 24, Fedora 25 ou Fedora 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-229">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="ddfca-230">Pour installer .NET Core pour Fedora 26, Fedora 25 (.NET Core 2.x) ou Fedora 24 (.NET Core 1.x) :</span><span class="sxs-lookup"><span data-stu-id="ddfca-230">To Install .NET Core for Fedora 26, Fedora 25 (.NET Core 2.x) or Fedora 24 (.NET Core 1.x):</span></span>

1. <span data-ttu-id="ddfca-231">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="ddfca-232">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="ddfca-232">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-233">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-233">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ddfca-234">**Fedora 26 ou Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="ddfca-234">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="ddfca-235">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="ddfca-235">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="ddfca-236">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="ddfca-236">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="ddfca-237">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-237">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="ddfca-238">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-238">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-239">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-239">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ddfca-240">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="ddfca-240">**Fedora 24**</span></span>

2. <span data-ttu-id="ddfca-241">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="ddfca-241">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="ddfca-242">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="ddfca-242">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="ddfca-243">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-243">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="ddfca-244">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-244">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="ddfca-245">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-245">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="ddfca-246">Installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-246">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="ddfca-247">Pour installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="ddfca-247">To Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="ddfca-248">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-248">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="ddfca-249">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="ddfca-249">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-250">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="ddfca-251">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="ddfca-251">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="ddfca-252">Ajoutez le flux de produit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ddfca-252">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="ddfca-253">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-253">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="ddfca-254">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-254">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-255">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-255">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="ddfca-256">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="ddfca-256">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="ddfca-257">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="ddfca-257">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="ddfca-258">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-258">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="ddfca-259">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-259">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="ddfca-260">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-260">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="ddfca-261">Installer .NET Core pour SUSE Linux Enterprise Server (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-261">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="ddfca-262">Pour installer .NET Core 2.x pour SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="ddfca-262">To Install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="ddfca-263">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-263">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="ddfca-264">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="ddfca-264">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="ddfca-265">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-265">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="ddfca-266">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-266">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="ddfca-267">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-267">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="ddfca-268">Installer .NET Core pour openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="ddfca-268">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="ddfca-269">Pour installer .NET Core 2.x pour openSUSE ou .NET Core 1.x pour openSUSE (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="ddfca-269">To Install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="ddfca-270">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-270">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="ddfca-271">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="ddfca-271">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ddfca-272">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-272">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="ddfca-273">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="ddfca-273">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="ddfca-274">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="ddfca-274">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="ddfca-275">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-275">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="ddfca-276">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-276">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ddfca-277">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ddfca-277">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="ddfca-278">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="ddfca-278">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="ddfca-279">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="ddfca-279">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="ddfca-280">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddfca-280">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="ddfca-281">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="ddfca-281">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="ddfca-282">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="ddfca-282">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="ddfca-283">En cas de problème avec l’installation de .NET Core 2.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0).</span><span class="sxs-lookup"><span data-stu-id="ddfca-283">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="ddfca-284">En cas de problème avec l’installation de .NET Core 1.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ou des [problèmes connus avec la version 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="ddfca-284">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>

