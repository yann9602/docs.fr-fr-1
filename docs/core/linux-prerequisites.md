---
title: "Prérequis pour .NET Core sur Linux"
description: "Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 04fdf26e150e6d489c0641588563f69f24835615
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="b40a0-104">Prérequis pour .NET Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="b40a0-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="b40a0-105">Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux.</span><span class="sxs-lookup"><span data-stu-id="b40a0-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="b40a0-106">Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :</span><span class="sxs-lookup"><span data-stu-id="b40a0-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="b40a0-107">Ligne de commande avec votre éditeur favori</span><span class="sxs-lookup"><span data-stu-id="b40a0-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="b40a0-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b40a0-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="b40a0-109">Versions de Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="b40a0-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="b40a0-111">.NET Core 2.0 traite Linux comme un seul système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b40a0-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="b40a0-112">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b40a0-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="b40a0-113">NET Core 2.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="b40a0-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="b40a0-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-115">CentOS 7</span></span>
 * <span data-ttu-id="b40a0-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="b40a0-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b40a0-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="b40a0-118">Debian 8.7 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b40a0-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="b40a0-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b40a0-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="b40a0-120">Linux Mint 18, Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="b40a0-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="b40a0-121">openSUSE 42.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b40a0-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="b40a0-122">SUSE Enterprise Linux (SLES) 12 SP2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b40a0-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="b40a0-123">Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="b40a0-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b40a0-125">.NET Core 1.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="b40a0-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="b40a0-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-127">CentOS 7</span></span>
* <span data-ttu-id="b40a0-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-128">Oracle Linux 7</span></span>
* <span data-ttu-id="b40a0-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="b40a0-129">Fedora 24</span></span>
* <span data-ttu-id="b40a0-130">Debian 8.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b40a0-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="b40a0-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="b40a0-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="b40a0-132">Ubuntu 16.10 est pris en charge par la dernière version de correctif logiciel de .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="b40a0-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="b40a0-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="b40a0-133">Linux Mint 17</span></span>
* <span data-ttu-id="b40a0-134">openSUSE 42.1 ou versions ultérieures (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="b40a0-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="b40a0-135">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="b40a0-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="b40a0-136">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="b40a0-136">Linux distribution dependencies</span></span>

<span data-ttu-id="b40a0-137">Les éléments suivants sont destinés à être des exemples.</span><span class="sxs-lookup"><span data-stu-id="b40a0-137">The following are intended to be examples.</span></span> <span data-ttu-id="b40a0-138">Les noms et les versions exactes peuvent varier légèrement sur votre distribution Linux de choix.</span><span class="sxs-lookup"><span data-stu-id="b40a0-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="b40a0-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="b40a0-139">Ubuntu</span></span>

<span data-ttu-id="b40a0-140">Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b40a0-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="b40a0-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="b40a0-141">libunwind8</span></span>
* <span data-ttu-id="b40a0-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="b40a0-142">liblttng-ust0</span></span>
* <span data-ttu-id="b40a0-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="b40a0-143">libcurl3</span></span>
* <span data-ttu-id="b40a0-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="b40a0-144">libssl1.0.0</span></span>
* <span data-ttu-id="b40a0-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="b40a0-145">libuuid1</span></span>
* <span data-ttu-id="b40a0-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="b40a0-146">libkrb5</span></span>
* <span data-ttu-id="b40a0-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="b40a0-147">zlib1g</span></span>
* <span data-ttu-id="b40a0-148">libicu52 (pour 14.X)</span><span class="sxs-lookup"><span data-stu-id="b40a0-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="b40a0-149">libicu55 (pour 16.X)</span><span class="sxs-lookup"><span data-stu-id="b40a0-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="b40a0-150">libicu57 (pour 17.X)</span><span class="sxs-lookup"><span data-stu-id="b40a0-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="b40a0-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="b40a0-151">CentOS</span></span>

<span data-ttu-id="b40a0-152">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b40a0-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="b40a0-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="b40a0-153">libunwind</span></span>
* <span data-ttu-id="b40a0-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="b40a0-154">lttng-ust</span></span>
* <span data-ttu-id="b40a0-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="b40a0-155">libcurl</span></span>
* <span data-ttu-id="b40a0-156">bibliothèques OpenSSL</span><span class="sxs-lookup"><span data-stu-id="b40a0-156">openssl-libs</span></span>
* <span data-ttu-id="b40a0-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="b40a0-157">libuuid</span></span>
* <span data-ttu-id="b40a0-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="b40a0-158">krb5-libs</span></span>
* <span data-ttu-id="b40a0-159">libicu</span><span class="sxs-lookup"><span data-stu-id="b40a0-159">libicu</span></span>
* <span data-ttu-id="b40a0-160">zlib</span><span class="sxs-lookup"><span data-stu-id="b40a0-160">zlib</span></span>

<span data-ttu-id="b40a0-161">Pour plus d’informations sur les dépendances, consultez [Applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (en anglais).</span><span class="sxs-lookup"><span data-stu-id="b40a0-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="b40a0-162">Installation des dépendances .NET Core avec les programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="b40a0-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="b40a0-163">Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b40a0-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="b40a0-164">Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur.</span><span class="sxs-lookup"><span data-stu-id="b40a0-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="b40a0-165">L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées.</span><span class="sxs-lookup"><span data-stu-id="b40a0-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="b40a0-166">En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="b40a0-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="b40a0-167">Sur Linux, il existe deux choix pour le package de programme d’installation :</span><span class="sxs-lookup"><span data-stu-id="b40a0-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="b40a0-168">Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="b40a0-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="b40a0-169">Utilisation des packages eux-mêmes, DEB ou RPM</span><span class="sxs-lookup"><span data-stu-id="b40a0-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="b40a0-170">Script d’installation avec le script de programme d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b40a0-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="b40a0-171">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="b40a0-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="b40a0-172">Vous pouvez télécharger le script à partir de : https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="b40a0-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="b40a0-173">Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives.</span><span class="sxs-lookup"><span data-stu-id="b40a0-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="b40a0-174">Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="b40a0-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40a0-175">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b40a0-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b40a0-176">Installer .NET Core pour Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b40a0-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b40a0-177">Pour installer .NET Core sur RHEL 7 :</span><span class="sxs-lookup"><span data-stu-id="b40a0-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="b40a0-178">Activez le canal Red Hat .NET, disponible dans votre abonnement RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="b40a0-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="b40a0-179">Pour Red Hat Enterprise Server 7, utilisez :</span><span class="sxs-lookup"><span data-stu-id="b40a0-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="b40a0-180">Pour Red Hat Enterprise 7 Workstation, utilisez :</span><span class="sxs-lookup"><span data-stu-id="b40a0-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="b40a0-181">Pour Red Hat Enterprise 7 HPC Compute Node, utilisez :</span><span class="sxs-lookup"><span data-stu-id="b40a0-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="b40a0-182">Installez l’outil scl.</span><span class="sxs-lookup"><span data-stu-id="b40a0-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="b40a0-183">Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="b40a0-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="b40a0-185">Installez le runtime et le kit SDK .NET Core 2.0 :</span><span class="sxs-lookup"><span data-stu-id="b40a0-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="b40a0-186">Activez le runtime/kit SDK .NET Core 2.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="b40a0-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b40a0-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="b40a0-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="b40a0-189">Installez le runtime et le kit SDK .NET Core 1.1 :</span><span class="sxs-lookup"><span data-stu-id="b40a0-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="b40a0-190">Activez le runtime et le kit SDK .NET Core 1.1 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="b40a0-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="b40a0-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="b40a0-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="b40a0-192">Installez le runtime et le kit SDK .NET Core 1.0 :</span><span class="sxs-lookup"><span data-stu-id="b40a0-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="b40a0-193">Activez le runtime et le kit SDK .NET Core 1.0 pour votre environnement :</span><span class="sxs-lookup"><span data-stu-id="b40a0-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="b40a0-194">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="b40a0-195">Pour obtenir de l’aide sur l’inscription à l’accès au canal Red Hat .NET, consultez le [chapitre 1 du guide de prise en main de .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) sur Red Hat.</span><span class="sxs-lookup"><span data-stu-id="b40a0-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="b40a0-196">Installer .NET Core pour Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10, Linux Mint 17 et Linux Mint 18 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="b40a0-197">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="b40a0-199">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="b40a0-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="b40a0-200">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="b40a0-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="b40a0-201">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="b40a0-201">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="b40a0-202">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="b40a0-202">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="b40a0-203">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="b40a0-203">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="b40a0-204">Installez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-204">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="b40a0-205">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-205">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-206">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-206">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="b40a0-207">Configurez le flux de package hôte de version souhaité.</span><span class="sxs-lookup"><span data-stu-id="b40a0-207">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="b40a0-208">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="b40a0-208">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="b40a0-209">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="b40a0-209">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="b40a0-210">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="b40a0-210">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="b40a0-211">Installez .NET Core 1.x sur Ubuntu ou Linux Mint :</span><span class="sxs-lookup"><span data-stu-id="b40a0-211">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="b40a0-212">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-212">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="b40a0-213">Installer .NET Core pour Debian 8 ou Debian 9 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-213">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="b40a0-214">Pour installer .NET Core sur Debian 8 ou Debian 9 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-214">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="b40a0-215">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-215">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="b40a0-216">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="b40a0-216">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-217">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-217">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="b40a0-218">Installez les composants du système.</span><span class="sxs-lookup"><span data-stu-id="b40a0-218">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="b40a0-219">Enregistrez la clé de produit Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="b40a0-219">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="b40a0-220">Enregistrez le flux de produit Microsoft approuvé.</span><span class="sxs-lookup"><span data-stu-id="b40a0-220">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="b40a0-221">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="b40a0-221">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="b40a0-222">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="b40a0-222">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="b40a0-223">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-223">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="b40a0-224">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-224">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="b40a0-225">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-225">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-226">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-226">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="b40a0-227">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="b40a0-227">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="b40a0-228">Téléchargez les fichiers binaires du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="b40a0-228">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="b40a0-229">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-229">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="b40a0-230">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-230">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="b40a0-231">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-231">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="b40a0-232">Installer .NET Core pour Fedora 24, Fedora 25 ou Fedora 26 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-232">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="b40a0-233">Pour installer .NET Core 2.x sur Fedora 26 ou Fedora 25, ou .NET Core 1.x sur Fedora 24 :</span><span class="sxs-lookup"><span data-stu-id="b40a0-233">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="b40a0-234">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-234">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="b40a0-235">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="b40a0-235">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-236">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="b40a0-237">**Fedora 26 ou Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="b40a0-237">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="b40a0-238">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="b40a0-238">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="b40a0-239">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="b40a0-239">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="b40a0-240">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-240">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="b40a0-241">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-241">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-242">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-242">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="b40a0-243">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="b40a0-243">**Fedora 24**</span></span>

2. <span data-ttu-id="b40a0-244">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="b40a0-244">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="b40a0-245">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="b40a0-245">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="b40a0-246">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-246">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="b40a0-247">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-247">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="b40a0-248">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-248">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="b40a0-249">Installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-249">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="b40a0-250">Pour installer .NET Core pour CentOS 7.1 (64 bits) et Oracle Linux 7.1 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-250">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="b40a0-251">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-251">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="b40a0-252">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="b40a0-252">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-253">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-253">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="b40a0-254">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="b40a0-254">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="b40a0-255">Ajoutez le flux de produit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b40a0-255">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="b40a0-256">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-256">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="b40a0-257">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-257">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-258">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-258">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="b40a0-259">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="b40a0-259">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="b40a0-260">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="b40a0-260">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="b40a0-261">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-261">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="b40a0-262">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-262">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="b40a0-263">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-263">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="b40a0-264">Installer .NET Core pour SUSE Linux Enterprise Server (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-264">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="b40a0-265">Pour installer .NET Core 2.x pour SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-265">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="b40a0-266">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-266">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="b40a0-267">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="b40a0-267">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="b40a0-268">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-268">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="b40a0-269">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-269">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="b40a0-270">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-270">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="b40a0-271">Installer .NET Core pour openSUSE (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b40a0-271">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="b40a0-272">Pour installer .NET Core 2.x pour openSUSE ou .NET Core 1.x pour openSUSE (64 bits) :</span><span class="sxs-lookup"><span data-stu-id="b40a0-272">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="b40a0-273">Supprimez du système toute **version antérieure** de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-273">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="b40a0-274">Un répertoire contrôlé par l’utilisateur est requis pour les installations du système Linux système depuis tar.gz.</span><span class="sxs-lookup"><span data-stu-id="b40a0-274">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b40a0-275">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-275">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="b40a0-276">Enregistrez la clé de signature Microsoft approuvée.</span><span class="sxs-lookup"><span data-stu-id="b40a0-276">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="b40a0-277">Ajoutez le flux de produit dotnet.</span><span class="sxs-lookup"><span data-stu-id="b40a0-277">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="b40a0-278">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-278">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="b40a0-279">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-279">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b40a0-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b40a0-280">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="b40a0-281">Vérifier les prérequis.</span><span class="sxs-lookup"><span data-stu-id="b40a0-281">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="b40a0-282">Téléchargez le fichier binaire du SDK .NET Core (tarball).</span><span class="sxs-lookup"><span data-stu-id="b40a0-282">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="b40a0-283">Extrayez les fichiers binaires du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b40a0-283">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="b40a0-284">Ajoutez dotnet au chemin.</span><span class="sxs-lookup"><span data-stu-id="b40a0-284">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="b40a0-285">Exécutez la commande `dotnet --version` pour vérifier que l’installation a réussi.</span><span class="sxs-lookup"><span data-stu-id="b40a0-285">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="b40a0-286">En cas de problème avec l’installation de .NET Core 2.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0).</span><span class="sxs-lookup"><span data-stu-id="b40a0-286">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="b40a0-287">En cas de problème avec l’installation de .NET Core 1.x sur une distribution/version Linux prise en charge, consultez la rubrique correspondante traitant des [problèmes connus avec la version 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ou des [problèmes connus avec la version 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="b40a0-287">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
