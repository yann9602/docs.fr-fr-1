---
title: Configuration requise pour .NET Core sur Windows
description: "Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core."
keywords: ".NET core, Windows, configuration requise, dépendances, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 06/26/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0e414af0edbafed5b7f540eda6de2e5078eac789
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="198e4-104">Configuration requise pour .NET Core sur Windows</span><span class="sxs-lookup"><span data-stu-id="198e4-104">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="198e4-105">Cet article détaille les dépendances nécessaires pour déployer et exécuter des applications .NET Core sur des machines Windows, et développer avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="198e4-105">This article shows you what dependencies you need to deploy and run .NET Core applications on Windows machines and develop using Visual Studio.</span></span>

## <a name="supported-windows-versions"></a><span data-ttu-id="198e4-106">Versions prises en charge de Windows</span><span class="sxs-lookup"><span data-stu-id="198e4-106">Supported Windows versions</span></span>

<span data-ttu-id="198e4-107">.NET Core est pris en charge par les versions suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="198e4-107">.NET Core is supported on the following versions of Windows:</span></span>

* <span data-ttu-id="198e4-108">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="198e4-108">Windows 7 SP1</span></span>
* <span data-ttu-id="198e4-109">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="198e4-109">Windows 8.1</span></span>
* <span data-ttu-id="198e4-110">Windows 10</span><span class="sxs-lookup"><span data-stu-id="198e4-110">Windows 10</span></span>
* <span data-ttu-id="198e4-111">Windows Server 2008 R2 SP1 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="198e4-111">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="198e4-112">Windows Server 2012 SP1 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="198e4-112">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="198e4-113">Windows Server 2012 R2 (version complète ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="198e4-113">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="198e4-114">Windows Server 2016 (version complète, Server Core ou Nano Server)</span><span class="sxs-lookup"><span data-stu-id="198e4-114">Windows Server 2016 (Full Server, Server Core or Nano Server)</span></span>

<span data-ttu-id="198e4-115">Consultez les [ notes de publication .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) pour plus d’informations sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="198e4-115">See the [.NET Core Release Notes](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) for the full set of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="198e4-116">Dépendances .NET Core</span><span class="sxs-lookup"><span data-stu-id="198e4-116">.NET Core dependencies</span></span>

<span data-ttu-id="198e4-117">.NET Core nécessite le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="198e4-117">.NET Core requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="198e4-118">Cette dépendance est installée automatiquement pour vous si vous utilisez le programme d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="198e4-118">This dependency is automatically installed for you if you use the .NET Core installer.</span></span> <span data-ttu-id="198e4-119">Toutefois, vous devez installer manuellement [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/en-us/download/details.aspx?id=52685) si vous installez .NET Core par le biais du [script d’installation](./tools/dotnet-install-script.md) ou si vous déployez une application .NET Core autonome.</span><span class="sxs-lookup"><span data-stu-id="198e4-119">However, you need to manually install the [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/en-us/download/details.aspx?id=52685) if you are installing .NET Core via the [installer script](./tools/dotnet-install-script.md) or deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="198e4-120"><em>Pour les machines Windows 7 et Windows Server 2008 uniquement :</em></span><span class="sxs-lookup"><span data-stu-id="198e4-120"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="198e4-121">Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2533623](https://support.microsoft.com/help/2533623) installé via Windows Update.</span><span class="sxs-lookup"><span data-stu-id="198e4-121">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="198e4-122">Prérequis pour Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="198e4-122">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="198e4-123">Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du kit de développement logiciel (SDK) .NET Core.</span><span class="sxs-lookup"><span data-stu-id="198e4-123">You can use any editor of your choice to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="198e4-124">Toutefois, si vous voulez développer des applications .NET Core sur Windows dans un environnement de développement intégré, vous pouvez utiliser [Visual Studio 2017](#visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="198e4-124">However, if you want to develop .NET Core applications on Windows in an integrated development environment, you can use [Visual Studio 2017](#visual-studio-2017).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="198e4-125">Même s’il est possible d’utiliser Visual Studio 2015 avec une version préliminaire des outils .NET Core, ces projets s’appuieront sur le fichier *project.json*, ce qui est maintenant déconseillé.</span><span class="sxs-lookup"><span data-stu-id="198e4-125">Even though, it's possible to use Visual Studio 2015 with a preview version of the .NET Core tooling, these projects will be *project.json*-based, which is now deprecated.</span></span> <span data-ttu-id="198e4-126">Visual Studio 2017 utilise des fichiers de projet basés sur MSBuild.</span><span class="sxs-lookup"><span data-stu-id="198e4-126">Visual Studio 2017 uses project files based on MSBuild.</span></span> <span data-ttu-id="198e4-127">Pour plus d’informations sur les changements de format, consultez la page [Vue d’ensemble de haut niveau des modifications](./tools/cli-msbuild-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="198e4-127">For more information about the format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

<span data-ttu-id="198e4-128">Pour utiliser Visual Studio 2017 afin de développer des applications .NET Core, vous devez installer la dernière version de Visual Studio en sélectionnant l’ensemble d’outils **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).</span><span class="sxs-lookup"><span data-stu-id="198e4-128">To use Visual Studio 2017 to develop .NET Core apps, you'll need to have the latest version of Visual Studio installed with the **.NET Core cross-platform development** toolset (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="198e4-129">![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="198e4-129">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>

<span data-ttu-id="198e4-130">Il existe différentes éditions de Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="198e4-130">There are different editions of Visual Studio 2017.</span></span> <span data-ttu-id="198e4-131">Vous pouvez télécharger [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) gratuitement pour commencer.</span><span class="sxs-lookup"><span data-stu-id="198e4-131">You can download [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) for free to get started.</span></span>  <span data-ttu-id="198e4-132">Pour en savoir plus sur le processus d'installation de Visual Studio, consultez [Installation de Visual Studio 2017](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="198e4-132">To learn more about the Visual Studio installation process, see [Install Visual Studio 2017](/visualstudio/install/install-visual-studio).</span></span>

<span data-ttu-id="198e4-133">Pour vérifier que vous exécutez la dernière version de Visual Studio 2017, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="198e4-133">To verify that you're running the latest version of Visual Studio 2017, do the following:</span></span>

 * <span data-ttu-id="198e4-134">Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="198e4-134">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
 * <span data-ttu-id="198e4-135">La boîte de dialogue **À propos de Microsoft Visual Studio** doit indiquer le numéro de version 15.0.26228.4 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="198e4-135">In the **About Microsoft Visual Studio** dialog, the version number should be 15.0.26228.4 or higher.</span></span>

<span data-ttu-id="198e4-136">Vous trouverez plus d’informations sur les modifications apportées à Visual Studio 2017 dans les [notes de publication](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="198e4-136">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>

