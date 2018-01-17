---
title: "Portage vers .NET Core - Utilisation du pack de compatibilité Windows"
description: "Découvrez le pack de compatibilité Windows et comment l’utiliser pour déplacer du code .NET Framework existant vers .NET Core"
keywords: ".NET, .NET Core, Windows, compatibilité"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 3b1fe02aad4f78499158ecb7fa9b8521cb7d992e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="62c81-104">Utilisation du pack de compatibilité Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="62c81-105">L’un des problèmes les plus courants auxquels les développeurs sont confrontés lors du portage de leur code existant vers .NET Core est qu’ils dépendent des API et des technologies qui existent uniquement dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62c81-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="62c81-106">Le *pack de compatibilité Windows* se rapporte à la mise à disposition d’un grand nombre de ces technologies afin que la création d’applications .NET Core et de bibliothèques .NET Standard devienne beaucoup plus viable pour le code existant.</span><span class="sxs-lookup"><span data-stu-id="62c81-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="62c81-107">Ce package est une [extension logique de.NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) qui augmente considérablement l’ensemble d’API et le code existant est compilé sans presque aucune modification.</span><span class="sxs-lookup"><span data-stu-id="62c81-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="62c81-108">Toutefois, pour respecter l’engagement de .NET Standard (« il s’agit de l’ensemble d’API fourni par toutes les implémentations .NET »), cela ne comprend pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le Registre, WMI (Windows Management Instrumentation), ou les API d’émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="62c81-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="62c81-109">Le *pack de compatibilité Windows* repose sur .NET Standard et permet d’accéder aux technologies Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="62c81-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="62c81-110">Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais envisagent de rester sur Windows pour commencer.</span><span class="sxs-lookup"><span data-stu-id="62c81-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="62c81-111">Dans ce scénario, le fait de ne pas pouvoir utiliser les technologies Windows uniquement est juste un obstacle à la migration sans aucun avantage en matière d’architecture.</span><span class="sxs-lookup"><span data-stu-id="62c81-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="62c81-112">Contenu du package</span><span class="sxs-lookup"><span data-stu-id="62c81-112">Package contents</span></span>

<span data-ttu-id="62c81-113">Le *pack de compatibilité Windows* est fourni via le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir de projets ciblant .NET Core ou .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="62c81-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="62c81-114">Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :</span><span class="sxs-lookup"><span data-stu-id="62c81-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="62c81-115">Pages de codes</span><span class="sxs-lookup"><span data-stu-id="62c81-115">Code Pages</span></span>
* <span data-ttu-id="62c81-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="62c81-116">CodeDom</span></span>
* <span data-ttu-id="62c81-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="62c81-117">Configuration</span></span>
* <span data-ttu-id="62c81-118">Services d'annuaire</span><span class="sxs-lookup"><span data-stu-id="62c81-118">Directory Services</span></span>
* <span data-ttu-id="62c81-119">Dessin</span><span class="sxs-lookup"><span data-stu-id="62c81-119">Drawing</span></span>
* <span data-ttu-id="62c81-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="62c81-120">ODBC</span></span>
* <span data-ttu-id="62c81-121">Autorisations</span><span class="sxs-lookup"><span data-stu-id="62c81-121">Permissions</span></span>
* <span data-ttu-id="62c81-122">Ports</span><span class="sxs-lookup"><span data-stu-id="62c81-122">Ports</span></span>
* <span data-ttu-id="62c81-123">Listes de contrôle d’accès Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="62c81-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="62c81-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="62c81-125">Chiffrement Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-125">Windows Cryptography</span></span>
* <span data-ttu-id="62c81-126">Journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-126">Windows EventLog</span></span>
* <span data-ttu-id="62c81-127">WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="62c81-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="62c81-128">Compteurs de performances Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-128">Windows Performance Counters</span></span>
* <span data-ttu-id="62c81-129">Registre Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-129">Windows Registry</span></span>
* <span data-ttu-id="62c81-130">Mise en cache Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="62c81-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="62c81-131">services Windows</span><span class="sxs-lookup"><span data-stu-id="62c81-131">Windows Services</span></span>

<span data-ttu-id="62c81-132">Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="62c81-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="62c81-133">Prise en main</span><span class="sxs-lookup"><span data-stu-id="62c81-133">Get started</span></span>

1. <span data-ttu-id="62c81-134">Avant le portage, veillez à examiner le [processus de portage](index.md).</span><span class="sxs-lookup"><span data-stu-id="62c81-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="62c81-135">Lors du portage du code existant vers .NET Core ou .NET Standard, installez le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="62c81-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="62c81-136">Si vous souhaitez rester sur Windows, vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="62c81-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="62c81-137">Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="62c81-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="62c81-138">Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :</span><span class="sxs-lookup"><span data-stu-id="62c81-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="62c81-139">Pour obtenir une démonstration, regardez la [vidéo de Channel 9 sur le pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="62c81-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

