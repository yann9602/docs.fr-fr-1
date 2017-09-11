---
title: "Utilisation du SDK et des outils .NET Core avec l’intégration continue"
description: "Informations sur l’utilisation du SDK .NET Core et de ses outils sur le serveur de builds."
keywords: ".NET, .NET Core, intégration continue, ci, build, automatisation, CI Travis, AppVeyor, Visual Studio Team Services, vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 67c08dd9804f6b51961be250033161427159e66e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="1d51d-104">Utilisation du SDK et des outils .NET Core avec l’intégration continue</span><span class="sxs-lookup"><span data-stu-id="1d51d-104">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="1d51d-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1d51d-105">Overview</span></span>

<span data-ttu-id="1d51d-106">Ce document décrit l’utilisation du SDK .NET Core et de ses outils sur un serveur de builds.</span><span class="sxs-lookup"><span data-stu-id="1d51d-106">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="1d51d-107">L’ensemble d’outils .NET Core fonctionne à la fois de manière interactive, où un développeur saisit des commandes dans une invite de commandes, et de manière automatique, où un serveur d’intégration continue (CI) exécute un script de build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-107">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="1d51d-108">Les commandes, les options, les entrées et les sorties sont identiques, et les seuls éléments que vous fournissez sont un moyen d’acquérir les outils et un système pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="1d51d-108">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="1d51d-109">Ce document se concentre sur les scénarios d’acquisition d’outils pour l’intégration continue. Il contient également des recommandations sur la façon de concevoir et de structurer vos scripts de build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-109">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="1d51d-110">Options d’installation pour les serveurs de builds avec intégration continue</span><span class="sxs-lookup"><span data-stu-id="1d51d-110">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="1d51d-111">Utilisation de programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="1d51d-111">Using the native installers</span></span>

<span data-ttu-id="1d51d-112">Les programmes d’installation natifs sont disponibles pour macOS, Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="1d51d-112">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="1d51d-113">Les programmes d’installation requièrent un accès administrateur (sudo) au serveur de builds.</span><span class="sxs-lookup"><span data-stu-id="1d51d-113">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="1d51d-114">L’avantage d’utiliser un programme d’installation natif est qu’il installe toutes les dépendances natives requises pour l’exécution des outils.</span><span class="sxs-lookup"><span data-stu-id="1d51d-114">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="1d51d-115">Les programmes d’installation natifs fournissent également une installation du kit SDK à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="1d51d-115">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="1d51d-116">Les utilisateurs de macOS doivent utiliser les programmes d’installation PKG.</span><span class="sxs-lookup"><span data-stu-id="1d51d-116">macOS users should use the PKG installers.</span></span> <span data-ttu-id="1d51d-117">Sous Linux, vous pouvez utiliser un gestionnaire de package basé sur les flux, tel que apt-get pour Ubuntu ou yum pour CentOS, ou vous pouvez utiliser directement les packages DEB ou RPM.</span><span class="sxs-lookup"><span data-stu-id="1d51d-117">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="1d51d-118">Sous Windows, utilisez le programme d’installation MSI.</span><span class="sxs-lookup"><span data-stu-id="1d51d-118">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="1d51d-119">Les fichiers binaires stables les plus récents se trouvent sous [Bien démarrer avec .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="1d51d-119">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="1d51d-120">Si vous souhaitez utiliser les outils en version préliminaire les plus récents (et potentiellement instables), utilisez les liens fournis dans le [référentiel GitHub dotnet/cli](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="1d51d-120">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="1d51d-121">Pour les distributions Linux, des archives `tar.gz` (également appelées `tarballs`) sont disponibles ; utilisez les scripts d’installation dans les archives pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d51d-121">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="1d51d-122">Utilisation du script d’installation</span><span class="sxs-lookup"><span data-stu-id="1d51d-122">Using the installer script</span></span>

<span data-ttu-id="1d51d-123">L’utilisation du script d’installation permet une installation non administrative sur votre serveur de builds, ainsi qu’une automatisation facile pour obtenir les outils.</span><span class="sxs-lookup"><span data-stu-id="1d51d-123">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="1d51d-124">Le script se charge de télécharger les outils et de les extraire dans un emplacement par défaut ou spécifié.</span><span class="sxs-lookup"><span data-stu-id="1d51d-124">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="1d51d-125">Vous pouvez également spécifier la version des outils que vous souhaitez installer et si vous voulez installer le kit SDK complet ou uniquement le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="1d51d-125">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="1d51d-126">Le script d’installation est automatisé pour s’exécuter au début de la génération afin de récupérer et d’installer la version nécessaire du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="1d51d-126">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="1d51d-127">La *version souhaitée* est la version du kit SDK dont vos projets ont besoin pour être générés.</span><span class="sxs-lookup"><span data-stu-id="1d51d-127">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="1d51d-128">Le script vous permet d’installer le kit SDK dans un répertoire local sur le serveur, d’exécuter les outils à partir de l’emplacement d’installation, puis de nettoyer (ou de laisser le service d’intégration continue nettoyer) une fois la génération terminée.</span><span class="sxs-lookup"><span data-stu-id="1d51d-128">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="1d51d-129">Cela fournit à l’ensemble de votre processus de génération l’encapsulation et l’isolation requises.</span><span class="sxs-lookup"><span data-stu-id="1d51d-129">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="1d51d-130">La documentation de référence sur le script d’installation est disponible dans la rubrique [dotnet-install](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1d51d-130">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="1d51d-131">Lorsque vous utilisez le script d’installation, les dépendances natives ne sont pas installées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1d51d-131">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="1d51d-132">Vous devez installer les dépendances natives si le système d’exploitation ne les possède pas.</span><span class="sxs-lookup"><span data-stu-id="1d51d-132">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="1d51d-133">Consultez la liste des prérequis dans la rubrique [Prérequis natifs .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="1d51d-133">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="1d51d-134">Exemples de configuration de l’intégration continue</span><span class="sxs-lookup"><span data-stu-id="1d51d-134">CI setup examples</span></span>

<span data-ttu-id="1d51d-135">Cette section décrit une configuration manuelle à l’aide d’un script PowerShell ou bash, et contient la description de plusieurs solutions d’intégration continue SaaS (logiciel en tant que service).</span><span class="sxs-lookup"><span data-stu-id="1d51d-135">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="1d51d-136">Les solutions d’intégration continue SaaS traitées sont [CI Travis](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) et [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span><span class="sxs-lookup"><span data-stu-id="1d51d-136">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="1d51d-137">Configuration manuelle</span><span class="sxs-lookup"><span data-stu-id="1d51d-137">Manual setup</span></span>

<span data-ttu-id="1d51d-138">Chaque service SaaS dispose de ses propres méthodes pour créer et configurer un processus de génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-138">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="1d51d-139">Si vous utilisez une solution SaaS différente de celles répertoriées ou si vous avez besoin d’une personnalisation qui va au-delà de la prise en charge prédéfinie, vous devez effectuer une configuration manuelle.</span><span class="sxs-lookup"><span data-stu-id="1d51d-139">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="1d51d-140">En règle générale, une configuration manuelle vous oblige à acquérir une version des outils (ou les versions les plus récentes des outils générées de nuit) et à exécuter votre script de build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-140">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="1d51d-141">Vous pouvez utiliser un script PowerShell ou bash pour orchestrer les commandes .NET Core ou vous pouvez utiliser un fichier projet qui décrit le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-141">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="1d51d-142">La [section sur l’orchestration](#orchestrating-the-build) fournit plus de détails sur ces options.</span><span class="sxs-lookup"><span data-stu-id="1d51d-142">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="1d51d-143">Après avoir créé un script qui exécute une configuration manuelle du serveur de builds CI, utilisez-le sur votre machine de développement afin de générer votre code localement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="1d51d-143">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="1d51d-144">Après avoir confirmé que le script s’exécute correctement localement, déployez-le sur votre serveur de builds CI.</span><span class="sxs-lookup"><span data-stu-id="1d51d-144">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="1d51d-145">Un script PowerShell relativement simple illustre comment obtenir le kit SDK .NET Core et l’installer sur un serveur de builds Windows :</span><span class="sxs-lookup"><span data-stu-id="1d51d-145">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the 
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the 
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it 
#   does, it's removed. This is not strictly required, but it's a 
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the 
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://raw.githubusercontent.com/dotnet/cli/rel/1.0.1/scripts/obtain/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the 
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the 
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="1d51d-146">Vous fournissez l’implémentation pour votre processus de génération à la fin du script.</span><span class="sxs-lookup"><span data-stu-id="1d51d-146">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="1d51d-147">Le script acquiert les outils, puis exécute votre processus de génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-147">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="1d51d-148">Pour les ordinateurs UNIX, le script bash suivant effectue les actions décrites dans le script PowerShell de la même manière :</span><span class="sxs-lookup"><span data-stu-id="1d51d-148">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
# Do not use an INSTALLDIR path containing spaces:
#   https://github.com/dotnet/cli/issues/5281
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://raw.githubusercontent.com/dotnet/cli/rel/1.0.1/scripts/obtain/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="1d51d-149">Intégration continue (CI) Travis</span><span class="sxs-lookup"><span data-stu-id="1d51d-149">Travis CI</span></span>

<span data-ttu-id="1d51d-150">Vous pouvez configurer [CI Travis](https://travis-ci.org/) pour installer le kit SDK .NET Core à l’aide du langage `csharp` et de la clé `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="1d51d-150">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="1d51d-151">Pour plus d’informations, consultez les documents officiels sur CI Travis sous [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) (Générer un projet C#, F# ou Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1d51d-151">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="1d51d-152">Remarque : lorsque vous accédez aux informations sur CI Travis, l’identificateur de langage `language: csharp` entretenu par la communauté fonctionne pour tous les langages .NET, notamment F# et Mono.</span><span class="sxs-lookup"><span data-stu-id="1d51d-152">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="1d51d-153">CI Travis exécute à la fois les travaux macOS (OS X 10.11, OS X 10.12) et Linux (Ubuntu 14.04) dans une *matrice de builds*, où vous spécifiez une combinaison de runtime, d’environnement et d’exclusions/inclusions pour couvrir les combinaisons de build pour votre application.</span><span class="sxs-lookup"><span data-stu-id="1d51d-153">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="1d51d-154">Pour plus d’informations, consultez le fichier [d’exemple .travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) et la rubrique sur la [personnalisation de la build](https://docs.travis-ci.com/user/customizing-the-build) dans la documentation CI Travis.</span><span class="sxs-lookup"><span data-stu-id="1d51d-154">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="1d51d-155">Les outils MSBuild incluent les runtimes LTS (1.0.x) et Current (1.1.x) dans le package ; donc, en installant le kit SDK, vous recevez tout ce dont vous avez besoin pour la génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-155">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="1d51d-156">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="1d51d-156">AppVeyor</span></span>

<span data-ttu-id="1d51d-157">[AppVeyor](https://www.appveyor.com/) installe le kit SDK .NET Core 1.0.1 avec l’image de travail de la build `Visual Studio 2017`.</span><span class="sxs-lookup"><span data-stu-id="1d51d-157">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="1d51d-158">D’autres images de la build avec des versions différentes du kit SDK .NET Core sont disponibles. Pour plus d’informations, consultez [l’exemple appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) et la rubrique [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) (Images de travail de la build) dans la documentation AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="1d51d-158">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="1d51d-159">Les fichiers binaires du kit SDK .NET Core sont téléchargés et décompressés dans un sous-répertoire à l’aide du script d’installation, puis ils sont ajoutés à la variable d’environnement `PATH`.</span><span class="sxs-lookup"><span data-stu-id="1d51d-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="1d51d-160">Ajoutez une matrice de builds pour exécuter des tests d’intégration avec plusieurs versions du SDK .NET Core :</span><span class="sxs-lookup"><span data-stu-id="1d51d-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="1d51d-161">Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="1d51d-161">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="1d51d-162">Configurez Visual Studio Team Services (VSTS) pour générer des projets .NET Core à l’aide de l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d51d-162">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="1d51d-163">Exécutez le script à partir de [l’étape de configuration manuelle](#manual-setup) en utilisant vos commandes.</span><span class="sxs-lookup"><span data-stu-id="1d51d-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="1d51d-164">Créez une build composée de plusieurs tâches de build intégrées VSTS qui sont configurées pour utiliser les outils .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d51d-164">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="1d51d-165">Les deux solutions sont valides.</span><span class="sxs-lookup"><span data-stu-id="1d51d-165">Both solutions are valid.</span></span> <span data-ttu-id="1d51d-166">À l’aide d’un script de configuration manuelle, vous contrôlez la version des outils que vous recevez, car vous les téléchargez dans le cadre de la génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="1d51d-167">La build est exécutée à partir d’un script que vous devez créer.</span><span class="sxs-lookup"><span data-stu-id="1d51d-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="1d51d-168">Cette rubrique couvre uniquement l’option manuelle.</span><span class="sxs-lookup"><span data-stu-id="1d51d-168">This topic only covers the manual option.</span></span> <span data-ttu-id="1d51d-169">Pour plus d’informations sur la composition d’une build avec des tâches de build VSTS, consultez la rubrique [Intégration et déploiement continus](https://www.visualstudio.com/docs/build/overview) de VSTS.</span><span class="sxs-lookup"><span data-stu-id="1d51d-169">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://www.visualstudio.com/docs/build/overview) topic.</span></span>

<span data-ttu-id="1d51d-170">Pour utiliser un script de configuration manuelle dans VSTS, créez une nouvelle définition de build et spécifiez le script à exécuter pour l’étape de génération.</span><span class="sxs-lookup"><span data-stu-id="1d51d-170">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="1d51d-171">Cette opération est possible grâce à l’interface utilisateur VSTS :</span><span class="sxs-lookup"><span data-stu-id="1d51d-171">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="1d51d-172">Commencez par créer une nouvelle définition de build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-172">Start by creating a new build definition.</span></span> <span data-ttu-id="1d51d-173">Lorsque vous atteignez l’écran qui vous permet de définir le type de build que vous souhaitez créer, sélectionnez l’option **Empty** (Vide).</span><span class="sxs-lookup"><span data-stu-id="1d51d-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Sélection d’une définition de build vide](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="1d51d-175">Après avoir configuré le référentiel à générer, vous êtes dirigé vers les définitions de la build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="1d51d-176">Sélectionnez **Ajouter une étape de build** :</span><span class="sxs-lookup"><span data-stu-id="1d51d-176">Select **Add build step**:</span></span>

   ![Ajout d’une étape de build](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="1d51d-178">Le **catalogue de tâches** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1d51d-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="1d51d-179">Le catalogue contient les tâches que vous utilisez dans la build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="1d51d-180">Étant donné que vous avez un script, sélectionnez le bouton **Ajouter** pour **PowerShell : exécuter un script PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1d51d-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Ajout d’une étape de script PowerShell](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="1d51d-182">Configurez l’étape de build.</span><span class="sxs-lookup"><span data-stu-id="1d51d-182">Configure the build step.</span></span> <span data-ttu-id="1d51d-183">Ajoutez le script à partir du référentiel que vous générez :</span><span class="sxs-lookup"><span data-stu-id="1d51d-183">Add the script from the repository that you're building:</span></span>

   ![Spécification du script PowerShell à exécuter](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="1d51d-185">Orchestration de la build</span><span class="sxs-lookup"><span data-stu-id="1d51d-185">Orchestrating the build</span></span>

<span data-ttu-id="1d51d-186">Ce document décrit principalement comment obtenir les outils .NET Core et configurer différents services d’intégration continue sans fournir d’informations sur la façon d’orchestrer ou de *réellement générer* votre code avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d51d-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="1d51d-187">Les choix sur la façon de structurer le processus de génération dépendent de nombreux facteurs qui ne peuvent pas être traités ici d’une manière générale.</span><span class="sxs-lookup"><span data-stu-id="1d51d-187">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="1d51d-188">Explorez les ressources et les exemples fournis dans la documentation de [CI Travis](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) et [VSTS](https://www.visualstudio.com/docs/build/overview) pour plus d’informations sur l’orchestration de vos builds avec chaque technologie.</span><span class="sxs-lookup"><span data-stu-id="1d51d-188">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://www.visualstudio.com/docs/build/overview) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="1d51d-189">L’utilisation directe de MSBuild ou l’utilisation des commandes de ligne de commande .NET Core constituent les deux méthodes générales que vous utilisez afin de structurer le processus de génération pour le code .NET Core à l’aide des outils .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d51d-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="1d51d-190">La méthode que vous choisissez dépend de votre niveau d’assurance et des compromis en matière de complexité.</span><span class="sxs-lookup"><span data-stu-id="1d51d-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="1d51d-191">MSBuild vous permet d’exprimer votre processus de génération sous la forme de tâches et de cibles, mais vous devez vous familiariser avec la syntaxe de fichier projet MSBuild complexe.</span><span class="sxs-lookup"><span data-stu-id="1d51d-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="1d51d-192">L’utilisation des outils de ligne de commande .NET Core est peut-être plus simple, mais vous devez écrire une logique d’orchestration dans un langage de script comme `bash` ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d51d-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d51d-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d51d-193">See also</span></span>

[<span data-ttu-id="1d51d-194">Étapes d’acquisition Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1d51d-194">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)   

