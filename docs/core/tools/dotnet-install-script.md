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

# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="ab2cb-104">Documentation sur les scripts dotnet-install</span><span class="sxs-lookup"><span data-stu-id="ab2cb-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="ab2cb-105">Nom</span><span class="sxs-lookup"><span data-stu-id="ab2cb-105">Name</span></span>

<span data-ttu-id="ab2cb-106">`dotnet-install.ps1` | `dotnet-install.sh` : script utilisé pour installer les outils de l’interface de ligne de commande (CLI) .NET Core et le runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core Command-line Interface (CLI) tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ab2cb-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="ab2cb-107">Synopsis</span></span>

<span data-ttu-id="ab2cb-108">Windows :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]`

<span data-ttu-id="ab2cb-109">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

## <a name="description"></a><span data-ttu-id="ab2cb-110">Description</span><span class="sxs-lookup"><span data-stu-id="ab2cb-110">Description</span></span>

<span data-ttu-id="ab2cb-111">Les scripts `dotnet-install` sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-111">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="ab2cb-112">Vous pouvez télécharger les scripts à partir du [référentiel GitHub sur les outils CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-112">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span> 

<span data-ttu-id="ab2cb-113">La principale utilité de ces scripts réside dans les scénarios d’automatisation et les installations non administrateur.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-113">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="ab2cb-114">Il existe deux scripts : un script PowerShell qui fonctionne sous Windows.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-114">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="ab2cb-115">L’autre script est un script bash fonctionnant sous Linux/OS X. Les deux scripts ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-115">The other script is a bash script that works on Linux/OS X. Both scripts have the same behavior.</span></span> <span data-ttu-id="ab2cb-116">Le script bash lit également les commutateurs PowerShell, pour vous permettre d’utiliser les commutateurs PowerShell avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-116">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/OS X systems.</span></span> 

<span data-ttu-id="ab2cb-117">Les scripts d’installation téléchargent le fichier ZIP/tarball à partir des cibles de builds CLI, puis poursuivent l’installation dans l’emplacement par défaut ou dans un emplacement spécifié par `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-117">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="ab2cb-118">Par défaut, les scripts d’installation téléchargent et installent le Kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-118">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="ab2cb-119">Si vous souhaitez obtenir uniquement le runtime partagé, spécifiez l’argument `--shared-runtime`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-119">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="ab2cb-120">Par défaut, le script ajoute l’emplacement d’installation $PATH pour la session active.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-120">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="ab2cb-121">Remplacez ce comportement par défaut en spécifiant l’argument `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-121">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="ab2cb-122">Avant d’exécuter le script, installez les [dépendances](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-122">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="ab2cb-123">Vous pouvez installer une version spécifique à l’aide de l’argument `--version`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-123">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="ab2cb-124">La version doit être spécifiée en trois parties (par exemple, 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-124">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="ab2cb-125">Si vous ne spécifiez pas de version, la valeur utilisée par défaut sera celle du premier fichier [global.json](global-json.md) trouvé dans la hiérarchie au-dessus du dossier dans lequel le script est appelé, et qui contient la propriété `version`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-125">If omitted, it defaults to the first [global.json](global-json.md) file found in the hierarchy above the folder where the script is invoked that contains the `version` property.</span></span> <span data-ttu-id="ab2cb-126">Si ce fichier n’est pas présent, la version la plus récente sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-126">If that isn't present, it will use the latest version.</span></span>

<span data-ttu-id="ab2cb-127">Vous pouvez également utiliser ce script pour obtenir le SDK ou les fichiers binaires de débogage de runtime partagé avec les symboles de débogage, à l’aide de l’argument `--debug`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-127">You can also use this script to obtain the SDK or shared runtime debug binaries with debug symbols by using the `--debug` argument.</span></span> <span data-ttu-id="ab2cb-128">Si vous n’effectuez pas cette opération lors de la première installation et réalisez ultérieurement que vous avez besoin des symboles de débogage, vous pouvez réexécuter le script avec l’argument `--debug` et la version du Kit de développement logiciel (SDK) installé pour obtenir les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-128">If you fail to do this on first install and realize later that you need the debug symbols, you can re-run the script with the `--debug` argument and the SDK version you installed to obtain the debug symbols.</span></span> 

## <a name="options"></a><span data-ttu-id="ab2cb-129">Options</span><span class="sxs-lookup"><span data-stu-id="ab2cb-129">Options</span></span>

<span data-ttu-id="ab2cb-130">Remarque : les options diffèrent d’une implémentation de script à l’autre.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-130">Note: Options are different between script implementations.</span></span> 

### <a name="powershell-windows"></a><span data-ttu-id="ab2cb-131">PowerShell (Windows)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-131">PowerShell (Windows)</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="ab2cb-132">Spécifie le canal source pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-132">Specifies the source channel for the installation.</span></span> <span data-ttu-id="ab2cb-133">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-133">The possible values are:</span></span>

- <span data-ttu-id="ab2cb-134">`Current` - Version actuelle</span><span class="sxs-lookup"><span data-stu-id="ab2cb-134">`Current` - Current release</span></span>
- <span data-ttu-id="ab2cb-135">`LTS` - Canal de prise en charge à long terme (version prise en charge actuelle)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-135">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="ab2cb-136">Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-136">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="ab2cb-137">Nom de la branche [par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` pour la version la plus récente de la branche `master` (versions nocturnes « bleeding edge »)]</span><span class="sxs-lookup"><span data-stu-id="ab2cb-137">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="ab2cb-138">La valeur par défaut est `LTS`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-138">The default value is `LTS`.</span></span> <span data-ttu-id="ab2cb-139">Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la rubrique [Cycle de prise en charge de .NET Core](https://www.microsoft.com/net/core/support).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-139">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="ab2cb-140">Représente une version de build sur le canal source (voir l’option `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-140">Represents a build version on the source channel (see the `-Channel` option).</span></span> <span data-ttu-id="ab2cb-141">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-141">The possible values are:</span></span>

- <span data-ttu-id="ab2cb-142">`latest` - Dernière build sur le canal</span><span class="sxs-lookup"><span data-stu-id="ab2cb-142">`latest` - Latest build on the channel</span></span>
- <span data-ttu-id="ab2cb-143">`coherent` - Dernière build cohérente sur le canal ; utilise la dernière combinaison de packages stable</span><span class="sxs-lookup"><span data-stu-id="ab2cb-143">`coherent` - Latest coherent build on the channel; uses the latest stable package combination</span></span>
- <span data-ttu-id="ab2cb-144">Version en trois parties au format X.Y.Z représentant une version de build spécifique (par exemple, `1.0.x`, où `x` représente la version corrective ; ou une build spécifique, par exemple `2.0.0-preview2-006120`)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-144">Three-part version in X.Y.Z format representing a specific build version (for example, `1.0.x` with `x` representing the patch version; or a specific build, such as `2.0.0-preview2-006120`)</span></span>

<span data-ttu-id="ab2cb-145">Si elle n’est pas spécifiée, la valeur utilisée par défaut pour `-Version` est celle du premier [global.json](global-json.md) qui contient le membre `version`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-145">If omitted, `-Version` defaults to the first [global.json](global-json.md) that contains the `version` member.</span></span> <span data-ttu-id="ab2cb-146">En l’absence de ce membre, la valeur par défaut de `-Version` est `latest`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-146">If that isn't present, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="ab2cb-147">Spécifie le chemin d’accès de l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-147">Specifies the installation path.</span></span> <span data-ttu-id="ab2cb-148">S’il n’existe pas déjà, le répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="ab2cb-149">La valeur par défaut est *% LocalAppData%\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-149">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="ab2cb-150">Remarque : Les fichiers binaires sont placés directement dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-150">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="ab2cb-151">Architecture des fichiers binaires .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="ab2cb-152">Les valeurs possibles sont `auto`, `x64` et `x86`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-152">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="ab2cb-153">La valeur par défaut est `auto`, qui représente l’architecture de système d’exploitation en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-153">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="ab2cb-154">S’il est défini, ce commutateur limite l’installation au runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-154">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="ab2cb-155">La totalité du SDK n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-155">The entire SDK isn't installed.</span></span>

<span data-ttu-id="ab2cb-156">`-DebugSymbols` (voir la REMARQUE)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-156">`-DebugSymbols` (see NOTE)</span></span>

<span data-ttu-id="ab2cb-157">Si cette option est définie, le programme d’installation inclut les symboles de débogage dans l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-157">If set, the installer includes debugging symbols in the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="ab2cb-158">Le commutateur `-DebugSymbols` n’est pas actuellement disponible, mais cela est prévu dans une prochaine version.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-158">The `-DebugSymbols` switch is not currently avaiable but planned for a future release.</span></span>

`-DryRun`

<span data-ttu-id="ab2cb-159">Si cette option est définie, le script n’effectue pas l’installation, mais affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-159">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="ab2cb-160">Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-160">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="ab2cb-161">Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-161">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="ab2cb-162">Si cette option est définie, le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-162">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="ab2cb-163">Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-163">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="ab2cb-164">Spécifie l’URL du flux Azure à utiliser par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-164">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="ab2cb-165">Il n’est pas recommandé de modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-165">It isn't recommended that you change this value.</span></span> <span data-ttu-id="ab2cb-166">La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-166">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="ab2cb-167">Si cette option est définie, le programme d’installation utilise le proxy pendant la création de demandes web.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-167">If set, the installer uses the proxy when making web requests.</span></span>

### <a name="bash-macoslinux"></a><span data-ttu-id="ab2cb-168">Interpréteur de commandes (Mac OS/Linux)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-168">Bash (macOS/Linux)</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

`-Channel <CHANNEL>`

<span data-ttu-id="ab2cb-169">Spécifie le canal source pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-169">Specifies the source channel for the installation.</span></span> <span data-ttu-id="ab2cb-170">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-170">The possible values are:</span></span>

- <span data-ttu-id="ab2cb-171">`Current` - Version actuelle</span><span class="sxs-lookup"><span data-stu-id="ab2cb-171">`Current` - Current release</span></span>
- <span data-ttu-id="ab2cb-172">`LTS` - Canal de prise en charge à long terme (version prise en charge actuelle)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-172">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="ab2cb-173">Version en deux parties au format X.Y représentant une version spécifique (par exemple, `2.0` ou `1.0`)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-173">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="ab2cb-174">Nom de la branche [par exemple, `release/2.0.0`, `release/2.0.0-preview2` ou `master` pour la version la plus récente de la branche `master` (versions nocturnes « bleeding edge »)]</span><span class="sxs-lookup"><span data-stu-id="ab2cb-174">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="ab2cb-175">La valeur par défaut est `LTS`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-175">The default value is `LTS`.</span></span> <span data-ttu-id="ab2cb-176">Pour plus d’informations sur les canaux de prise en charge de .NET, consultez la rubrique [Cycle de prise en charge de .NET Core](https://www.microsoft.com/net/core/support).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-176">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="ab2cb-177">Représente une version de build sur le canal source (voir l’option `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="ab2cb-177">Represents a build version on the source channel (see the `-Channel` option).</span></span> <span data-ttu-id="ab2cb-178">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-178">The possible values are:</span></span>

- <span data-ttu-id="ab2cb-179">`latest` - Dernière build sur le canal</span><span class="sxs-lookup"><span data-stu-id="ab2cb-179">`latest` - Latest build on the channel</span></span>
- <span data-ttu-id="ab2cb-180">`coherent` - Dernière build cohérente sur le canal ; utilise la dernière combinaison de packages stable</span><span class="sxs-lookup"><span data-stu-id="ab2cb-180">`coherent` - Latest coherent build on the channel; uses the latest stable package combination</span></span>
- <span data-ttu-id="ab2cb-181">Version en trois parties au format X.Y.Z représentant une version de build spécifique (par exemple, `1.0.x`, où `x` représente la version corrective ; ou une build spécifique, par exemple `2.0.0-preview2-006120`)</span><span class="sxs-lookup"><span data-stu-id="ab2cb-181">Three-part version in X.Y.Z format representing a specific build version (for example, `1.0.x` with `x` representing the patch version; or a specific build, such as `2.0.0-preview2-006120`)</span></span>

<span data-ttu-id="ab2cb-182">Si elle n’est pas spécifiée, la valeur utilisée par défaut pour `-Version` est celle du premier [global.json](global-json.md) qui contient le membre `version`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-182">If omitted, `-Version` defaults to the first [global.json](global-json.md) that contains the `version` member.</span></span> <span data-ttu-id="ab2cb-183">En l’absence de ce membre, la valeur par défaut de `-Version` est `latest`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-183">If that isn't present, `-Version` defaults to `latest`.</span></span>

`--install-dir <DIRECTORY>`

<span data-ttu-id="ab2cb-184">Spécifie le chemin d’accès de l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-184">Specifies the installation path.</span></span> <span data-ttu-id="ab2cb-185">S’il n’existe pas déjà, le répertoire est créé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-185">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="ab2cb-186">La valeur par défaut est `$HOME/.dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-186">The default value is `$HOME/.dotnet`.</span></span>

`--architecture <ARCHITECTURE>`

<span data-ttu-id="ab2cb-187">Architecture des fichiers binaires .NET Core à installer.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-187">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="ab2cb-188">Les valeurs possibles sont `auto`, `x64` et `amd64`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-188">Possible values are `auto`, `x64` and `amd64`.</span></span> <span data-ttu-id="ab2cb-189">La valeur par défaut est `auto`, qui représente l’architecture de système d’exploitation en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-189">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`--shared-runtime`

<span data-ttu-id="ab2cb-190">S’il est défini, ce commutateur limite l’installation au runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-190">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="ab2cb-191">La totalité du SDK n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-191">The entire SDK isn't installed.</span></span>

`--debug-symbols`

<span data-ttu-id="ab2cb-192">Si cette option est définie, le programme d’installation inclut les symboles de débogage dans l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-192">If set, the installer includes debugging symbols in the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="ab2cb-193">Ce commutateur n’est pas actuellement disponible, mais cela est prévu dans une prochaine version.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-193">This switch is not currently avaiable but planned for a future release.</span></span>

`--dry-run`

<span data-ttu-id="ab2cb-194">Si cette option est définie, le script n’effectue pas l’installation, mais affiche à la place la ligne de commande à utiliser pour installer la version de l’interface CLI .NET Core actuellement demandée.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-194">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="ab2cb-195">Par exemple, si vous spécifiez la version `latest`, elle affiche un lien avec la version spécifique, pour que cette commande puisse être utilisée de façon déterministe dans un script de génération.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-195">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="ab2cb-196">Elle affiche également l’emplacement du fichier binaire si vous préférez l’installer ou le télécharger vous-même.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-196">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`--no-path`

<span data-ttu-id="ab2cb-197">Si cette option est définie, le préfixe /installdir n’est pas exporté dans le chemin de la session actuelle.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-197">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="ab2cb-198">Par défaut, le script modifie le chemin, ce qui rend les outils CLI disponibles immédiatement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-198">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`--verbose`

<span data-ttu-id="ab2cb-199">Affiche les informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-199">Display diagnostics information.</span></span>

`--azure-feed`

<span data-ttu-id="ab2cb-200">Spécifie l’URL du flux Azure à utiliser par ce programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-200">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="ab2cb-201">Il n’est pas recommandé de modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-201">It isn't recommended that you change this value.</span></span> <span data-ttu-id="ab2cb-202">La valeur par défaut est `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-202">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`--help`

<span data-ttu-id="ab2cb-203">Affiche l’aide pour le script.</span><span class="sxs-lookup"><span data-stu-id="ab2cb-203">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="ab2cb-204">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2cb-204">Examples</span></span>

<span data-ttu-id="ab2cb-205">Installez la dernière version de développement à l’emplacement par défaut :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-205">Install the latest development version to the default location:</span></span>

<span data-ttu-id="ab2cb-206">Windows :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-206">Windows:</span></span>

`./dotnet-install.ps1 -Channel Future`

<span data-ttu-id="ab2cb-207">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-207">macOS/Linux:</span></span>

`./dotnet-install.sh --channel Future`

<span data-ttu-id="ab2cb-208">Installez la dernière préversion à l’emplacement spécifié :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-208">Install the latest preview to the specified location:</span></span>

<span data-ttu-id="ab2cb-209">Windows :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-209">Windows:</span></span>

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

<span data-ttu-id="ab2cb-210">Mac OS/Linux :</span><span class="sxs-lookup"><span data-stu-id="ab2cb-210">macOS/Linux:</span></span>

`./dotnet-install.sh --channel preview --install-dir ~/cli`

## <a name="see-also"></a><span data-ttu-id="ab2cb-211">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab2cb-211">See also</span></span>

<span data-ttu-id="ab2cb-212">[Versions de .NET Core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="ab2cb-212">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="ab2cb-213">Archive de téléchargement de .NET Core Runtime et du Kit SDK</span><span class="sxs-lookup"><span data-stu-id="ab2cb-213">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

