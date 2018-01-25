---
title: "Prérequis pour .NET Core sur Linux"
description: "Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: d3c5dde443f848831f7c0585633339c35213357b
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="6d50d-104">Prérequis pour .NET Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="6d50d-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="6d50d-105">Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux.</span><span class="sxs-lookup"><span data-stu-id="6d50d-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="6d50d-106">Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :</span><span class="sxs-lookup"><span data-stu-id="6d50d-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="6d50d-107">Ligne de commande avec votre éditeur favori</span><span class="sxs-lookup"><span data-stu-id="6d50d-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="6d50d-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6d50d-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="6d50d-109">Versions de Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="6d50d-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6d50d-111">.NET Core 2.0 traite Linux comme un seul système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6d50d-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="6d50d-112">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6d50d-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="6d50d-113">NET Core 2.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="6d50d-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="6d50d-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-115">CentOS 7</span></span>
 * <span data-ttu-id="6d50d-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="6d50d-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="6d50d-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="6d50d-118">Debian 8.7 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6d50d-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="6d50d-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d50d-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="6d50d-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="6d50d-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="6d50d-121">openSUSE 42.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6d50d-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="6d50d-122">SUSE Enterprise Linux (SLES) 12 SP2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6d50d-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="6d50d-123">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="6d50d-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6d50d-125">.NET Core 1.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="6d50d-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="6d50d-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-127">CentOS 7</span></span>
* <span data-ttu-id="6d50d-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-128">Oracle Linux 7</span></span>
* <span data-ttu-id="6d50d-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="6d50d-129">Fedora 24</span></span>
* <span data-ttu-id="6d50d-130">Debian 8.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6d50d-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="6d50d-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="6d50d-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="6d50d-132">Ubuntu 16.10 est pris en charge par la dernière version de correctif logiciel de .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="6d50d-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="6d50d-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="6d50d-133">Linux Mint 17</span></span>
* <span data-ttu-id="6d50d-134">openSUSE 42.1 ou versions ultérieures (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="6d50d-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="6d50d-135">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="6d50d-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="6d50d-136">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="6d50d-136">Linux distribution dependencies</span></span>

<span data-ttu-id="6d50d-137">Les éléments suivants sont destinés à être des exemples.</span><span class="sxs-lookup"><span data-stu-id="6d50d-137">The following are intended to be examples.</span></span> <span data-ttu-id="6d50d-138">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="6d50d-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="6d50d-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6d50d-139">Ubuntu</span></span>

<span data-ttu-id="6d50d-140">Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d50d-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="6d50d-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="6d50d-141">libunwind8</span></span>
* <span data-ttu-id="6d50d-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="6d50d-142">liblttng-ust0</span></span>
* <span data-ttu-id="6d50d-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="6d50d-143">libcurl3</span></span>
* <span data-ttu-id="6d50d-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="6d50d-144">libssl1.0.0</span></span>
* <span data-ttu-id="6d50d-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="6d50d-145">libuuid1</span></span>
* <span data-ttu-id="6d50d-146">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="6d50d-146">libkrb5-3</span></span>
* <span data-ttu-id="6d50d-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="6d50d-147">zlib1g</span></span>
* <span data-ttu-id="6d50d-148">libicu52 (pour 14.X)</span><span class="sxs-lookup"><span data-stu-id="6d50d-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="6d50d-149">libicu55 (pour 16.X)</span><span class="sxs-lookup"><span data-stu-id="6d50d-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="6d50d-150">libicu57 (pour 17.X)</span><span class="sxs-lookup"><span data-stu-id="6d50d-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="6d50d-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="6d50d-151">CentOS</span></span>

<span data-ttu-id="6d50d-152">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d50d-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="6d50d-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="6d50d-153">libunwind</span></span>
* <span data-ttu-id="6d50d-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="6d50d-154">lttng-ust</span></span>
* <span data-ttu-id="6d50d-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="6d50d-155">libcurl</span></span>
* <span data-ttu-id="6d50d-156">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="6d50d-156">openssl-libs</span></span>
* <span data-ttu-id="6d50d-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="6d50d-157">libuuid</span></span>
* <span data-ttu-id="6d50d-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="6d50d-158">krb5-libs</span></span>
* <span data-ttu-id="6d50d-159">libicu</span><span class="sxs-lookup"><span data-stu-id="6d50d-159">libicu</span></span>
* <span data-ttu-id="6d50d-160">zlib</span><span class="sxs-lookup"><span data-stu-id="6d50d-160">zlib</span></span>

<span data-ttu-id="6d50d-161">Pour plus d’informations sur les dépendances, consultez [Applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (en anglais).</span><span class="sxs-lookup"><span data-stu-id="6d50d-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="6d50d-162">Installation des dépendances .NET Core avec les programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="6d50d-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="6d50d-163">Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6d50d-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="6d50d-164">Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur.</span><span class="sxs-lookup"><span data-stu-id="6d50d-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="6d50d-165">L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées.</span><span class="sxs-lookup"><span data-stu-id="6d50d-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="6d50d-166">En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="6d50d-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="6d50d-167">Sur Linux, il existe deux choix pour le package de programme d’installation :</span><span class="sxs-lookup"><span data-stu-id="6d50d-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="6d50d-168">Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="6d50d-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="6d50d-169">Utilisation des packages eux-mêmes, DEB ou RPM</span><span class="sxs-lookup"><span data-stu-id="6d50d-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="6d50d-170">Script d’installation avec le script de programme d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d50d-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="6d50d-171">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="6d50d-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="6d50d-172">Vous pouvez télécharger le script à partir de : https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="6d50d-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="6d50d-173">Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives.</span><span class="sxs-lookup"><span data-stu-id="6d50d-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="6d50d-174">Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="6d50d-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d50d-175">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="6d50d-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6d50d-176">Installer .NET Core pour Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6d50d-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6d50d-177">Pour installer .NET Core sur RHEL 7 :</span><span class="sxs-lookup"><span data-stu-id="6d50d-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="6d50d-178">Activez le canal Red Hat .NET, disponible dans votre abonnement RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="6d50d-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="6d50d-179">Pour Red Hat Enterprise Server 7, utilisez :</span><span class="sxs-lookup"><span data-stu-id="6d50d-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="6d50d-180">Pour Red Hat Enterprise 7 Workstation, utilisez :</span><span class="sxs-lookup"><span data-stu-id="6d50d-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="6d50d-181">Pour Red Hat Enterprise 7 HPC Compute Node, utilisez :</span><span class="sxs-lookup"><span data-stu-id="6d50d-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="6d50d-182">Installez l’outil scl.</span><span class="sxs-lookup"><span data-stu-id="6d50d-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="6d50d-183">Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d50d-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6d50d-185">Installez le runtime et le kit SDK .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="6d50d-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="6d50d-186">Activez le runtime/kit SDK .NET Core 2.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="6d50d-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6d50d-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="6d50d-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="6d50d-189">Installez le runtime et le kit SDK .NET Core 1.1 :</span><span class="sxs-lookup"><span data-stu-id="6d50d-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="6d50d-190">Activez le runtime et le kit SDK .NET Core 1.1 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="6d50d-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="6d50d-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="6d50d-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="6d50d-192">Installez le runtime et le kit SDK .NET Core 1.0 :</span><span class="sxs-lookup"><span data-stu-id="6d50d-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="6d50d-193">Activez le runtime et le kit SDK .NET Core 1.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="6d50d-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="6d50d-194">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="6d50d-195">Pour obtenir de l’aide sur l’inscription à l’accès au canal Red Hat .NET, consultez le [chapitre 1 du guide de prise en main de .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) sur Red Hat.</span><span class="sxs-lookup"><span data-stu-id="6d50d-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="6d50d-196">Installer .NET Core pour Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10, Linux Mint 17 et Linux Mint 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="6d50d-197">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="6d50d-199">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="6d50d-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="6d50d-200">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="6d50d-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="6d50d-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="6d50d-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="6d50d-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="6d50d-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="6d50d-203">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="6d50d-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="6d50d-204">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="6d50d-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="6d50d-205">Installez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. <span data-ttu-id="6d50d-206">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-207">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="6d50d-208">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="6d50d-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="6d50d-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="6d50d-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="6d50d-210">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="6d50d-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="6d50d-211">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="6d50d-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="6d50d-212">Installez .NET Core 1.x sur Ubuntu ou Linux Mint :</span><span class="sxs-lookup"><span data-stu-id="6d50d-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="6d50d-213">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="6d50d-214">Installer .NET Core pour Debian 8 ou Debian 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="6d50d-215">Pour installer .NET Core sur Debian 8 ou Debian 9 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="6d50d-216">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="6d50d-217">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="6d50d-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="6d50d-219">Installez les composants du système.</span><span class="sxs-lookup"><span data-stu-id="6d50d-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="6d50d-220">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="6d50d-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="6d50d-221">Enregistrez le flux de produit Microsoft approuvé.</span><span class="sxs-lookup"><span data-stu-id="6d50d-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="6d50d-222">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="6d50d-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="6d50d-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="6d50d-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="6d50d-224">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="6d50d-225">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="6d50d-226">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="6d50d-228">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="6d50d-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="6d50d-229">Téléchargez les fichiers binaires du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="6d50d-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="6d50d-230">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="6d50d-231">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="6d50d-232">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="6d50d-233">Installer .NET Core pour Fedora 24, Fedora 25 ou Fedora 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="6d50d-234">Pour installer .NET Core 2.x sur Fedora 26 ou Fedora 25, ou .NET Core 1.x sur Fedora 24 :</span><span class="sxs-lookup"><span data-stu-id="6d50d-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="6d50d-235">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="6d50d-236">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="6d50d-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6d50d-238">**Fedora 26 ou Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="6d50d-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="6d50d-239">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="6d50d-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="6d50d-240">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="6d50d-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="6d50d-241">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="6d50d-242">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-243">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6d50d-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="6d50d-244">**Fedora 24**</span></span>

2. <span data-ttu-id="6d50d-245">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="6d50d-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="6d50d-246">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="6d50d-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="6d50d-247">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="6d50d-248">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="6d50d-249">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="6d50d-250">Installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="6d50d-251">Pour installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="6d50d-252">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="6d50d-253">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="6d50d-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="6d50d-255">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="6d50d-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="6d50d-256">Ajoutez le flux de produit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6d50d-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="6d50d-257">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="6d50d-258">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-259">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="6d50d-260">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="6d50d-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="6d50d-261">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="6d50d-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="6d50d-262">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="6d50d-263">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="6d50d-264">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="6d50d-265">Installer .NET Core pour SUSE Linux Enterprise Server (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="6d50d-266">Pour installer .NET Core 2.x pour SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="6d50d-267">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="6d50d-268">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="6d50d-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="6d50d-269">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="6d50d-270">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="6d50d-271">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="6d50d-272">Installer .NET Core pour openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="6d50d-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="6d50d-273">Pour installer .NET Core 2.x pour openSUSE ou .NET Core 1.x pour openSUSE (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="6d50d-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="6d50d-274">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="6d50d-275">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="6d50d-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d50d-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="6d50d-277">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="6d50d-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="6d50d-278">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="6d50d-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="6d50d-279">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="6d50d-280">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d50d-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d50d-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="6d50d-282">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="6d50d-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="6d50d-283">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="6d50d-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="6d50d-284">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6d50d-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="6d50d-285">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="6d50d-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="6d50d-286">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d50d-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="6d50d-287">En cas de problème avec l’installation de .NET Core 2.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0).</span><span class="sxs-lookup"><span data-stu-id="6d50d-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="6d50d-288">En cas de problème avec l’installation de .NET Core 1.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ou des [problèmes connus avec la version 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6d50d-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
