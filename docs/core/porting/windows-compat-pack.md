---
title: "Portage vers le .NET Core - le Pack de compatibilité de Windows"
description: "En savoir plus sur le Pack de compatibilité de Windows et comment utiliser pour porter du code .NET Framework existant vers le .NET Core"
keywords: ".NET, .NET core, Windows, compatibilité"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="09a73-104">Le Pack de compatibilité de Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="09a73-105">Un des problèmes plus courants auxquels les développeurs sont confrontés lors du portage de leur code existant vers le .NET Core est que celles-ci dépendent API et des technologies qui existent uniquement dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09a73-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="09a73-106">Le *Pack de compatibilité Windows* est sur la fourniture de ces technologies, afin que la création d’applications de base de .NET, ainsi que les bibliothèques .NET Standard redevient beaucoup plus de code existant.</span><span class="sxs-lookup"><span data-stu-id="09a73-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="09a73-107">Ce package est un opérateur logique [extension Standard de .NET 2.0](../whats-new/index.md#api-changes-and-library-support) que considérablement ensemble d’API augmente et le code existant se compile presque sans modification.</span><span class="sxs-lookup"><span data-stu-id="09a73-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="09a73-108">Mais pour maintenir la promesse de .NET Standard (« il est le jeu d’API qui permettent de toutes les implémentations de .NET »), cela n’a pas été inclut des technologies qui peuvent ne pas fonctionner sur toutes les plateformes, telles que le Registre, Windows Management Instrumentation (WMI), ou l’émission de réflexion API.</span><span class="sxs-lookup"><span data-stu-id="09a73-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="09a73-109">Le *Pack de compatibilité Windows* reposant sur .NET Standard et donne accès aux technologies Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="09a73-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="09a73-110">Il est particulièrement utile pour les clients want déplacer vers le .NET Core mais plan à rester sur Windows en tant que première étape.</span><span class="sxs-lookup"><span data-stu-id="09a73-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="09a73-111">Dans ce scénario, n’est ne pas en mesure d’utiliser les technologies Windows uniquement est uniquement un obstacle migration avec zéro avantages architecturales.</span><span class="sxs-lookup"><span data-stu-id="09a73-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="09a73-112">Contenu du package</span><span class="sxs-lookup"><span data-stu-id="09a73-112">Package contents</span></span>

<span data-ttu-id="09a73-113">Le *Pack de compatibilité Windows* est fourni via le NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencée à partir de projets ciblant .NET Core ou .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="09a73-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="09a73-114">Il fournit environ 20 000 API, y compris les API Windows uniquement, ainsi qu’inter-plateformes dans les domaines technologiques suivants :</span><span class="sxs-lookup"><span data-stu-id="09a73-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="09a73-115">Pages de codes</span><span class="sxs-lookup"><span data-stu-id="09a73-115">Code Pages</span></span>
* <span data-ttu-id="09a73-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="09a73-116">CodeDom</span></span>
* <span data-ttu-id="09a73-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="09a73-117">Configuration</span></span>
* <span data-ttu-id="09a73-118">Services d'annuaire</span><span class="sxs-lookup"><span data-stu-id="09a73-118">Directory Services</span></span>
* <span data-ttu-id="09a73-119">dessin</span><span class="sxs-lookup"><span data-stu-id="09a73-119">Drawing</span></span>
* <span data-ttu-id="09a73-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="09a73-120">ODBC</span></span>
* <span data-ttu-id="09a73-121">Autorisations</span><span class="sxs-lookup"><span data-stu-id="09a73-121">Permissions</span></span>
* <span data-ttu-id="09a73-122">Ports</span><span class="sxs-lookup"><span data-stu-id="09a73-122">Ports</span></span>
* <span data-ttu-id="09a73-123">Listes de contrôle d’accès (ACL) Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="09a73-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="09a73-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="09a73-125">Chiffrement de Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-125">Windows Cryptography</span></span>
* <span data-ttu-id="09a73-126">Journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-126">Windows EventLog</span></span>
* <span data-ttu-id="09a73-127">WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="09a73-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="09a73-128">Compteurs de performances Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-128">Windows Performance Counters</span></span>
* <span data-ttu-id="09a73-129">Registre Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-129">Windows Registry</span></span>
* <span data-ttu-id="09a73-130">La mise en cache du Runtime Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="09a73-131">services Windows</span><span class="sxs-lookup"><span data-stu-id="09a73-131">Windows Services</span></span>

<span data-ttu-id="09a73-132">Pour plus d’informations, consultez la [spec du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="09a73-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="09a73-133">Prise en main</span><span class="sxs-lookup"><span data-stu-id="09a73-133">Get started</span></span>

1. <span data-ttu-id="09a73-134">Avant de porter, veillez à examiner le [processus de portage](index.md).</span><span class="sxs-lookup"><span data-stu-id="09a73-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="09a73-135">Lors du portage du code existant vers .NET Core ou .NET Standard, installez le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="09a73-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="09a73-136">Si vous souhaitez rester sur Windows, vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="09a73-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="09a73-137">Si vous souhaitez exécuter l’application .NET Core ou une bibliothèque .NET Standard sur Linux ou macOS, utilisez le [API analyseur](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) pour rechercher l’utilisation des API qui ne fonctionne pas inter-plateformes.</span><span class="sxs-lookup"><span data-stu-id="09a73-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="09a73-138">Supprimez les utilisations de ces API, remplacez-les par inter-plateformes alternatives ou protéger à l’aide d’une vérification de la plateforme, telles que :</span><span class="sxs-lookup"><span data-stu-id="09a73-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="09a73-139">Pour une démonstration, passez en revue les [vidéo de Channel 9 du Pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="09a73-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

