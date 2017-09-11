---
title: "Télémétrie des outils .NET Core"
description: "Découvrez les fonctionnalités de télémétrie des outils .NET Core, qui collectent des informations d’utilisation à des fins d’analyse."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1816b9fbad1f671820c9f970674c8af2147a230e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-tools-telemetry"></a><span data-ttu-id="0eb08-104">Télémétrie des outils .NET Core</span><span class="sxs-lookup"><span data-stu-id="0eb08-104">.NET Core Tools Telemetry</span></span>

<span data-ttu-id="0eb08-105">Les outils .NET Core incluent une [fonctionnalité de télémétrie](https://github.com/dotnet/cli/pull/2145) qui recueille des informations d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="0eb08-105">The .NET Core Tools include a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="0eb08-106">Il est important pour l’équipe .NET de comprendre la façon dont les outils sont utilisés, afin de pouvoir les améliorer.</span><span class="sxs-lookup"><span data-stu-id="0eb08-106">It’s important that the .NET Team understands how the tools are being used so that we can improve them.</span></span>

<span data-ttu-id="0eb08-107">Les données collectées sont anonymes, et sont destinées à être regroupées, puis publiées par les ingénieurs Microsoft et les ingénieurs de la communauté, sous la [licence Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="0eb08-107">The data collected is anonymous and will be published in an aggregated form for use by both Microsoft and community engineers under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="0eb08-108">Portée</span><span class="sxs-lookup"><span data-stu-id="0eb08-108">Scope</span></span>

<span data-ttu-id="0eb08-109">La commande `dotnet` permet de lancer des applications et les outils .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0eb08-109">The `dotnet` command is used to launch both apps and the .NET Core Tools.</span></span> <span data-ttu-id="0eb08-110">La commande `dotnet` ne permet pas de collecter des données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="0eb08-110">The `dotnet` command itself does not collect telemetry.</span></span> <span data-ttu-id="0eb08-111">Ce sont les outils .NET Core, qui sont exécutés via la commande `dotnet`, qui collectent les données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="0eb08-111">It is the .NET Core Tools that are run via the `dotnet` command that collect telemetry.</span></span>

<span data-ttu-id="0eb08-112">Commandes .NET Core (télémétrie non activée) :</span><span class="sxs-lookup"><span data-stu-id="0eb08-112">.NET Core commands (telemetry is not enabled):</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="0eb08-113">[Commandes](index.md) des outils .NET Core (télémétrie activée) :</span><span class="sxs-lookup"><span data-stu-id="0eb08-113">.NET Core Tools [commands](index.md) (telemetry is enabled), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="behavior"></a><span data-ttu-id="0eb08-114">Comportement</span><span class="sxs-lookup"><span data-stu-id="0eb08-114">Behavior</span></span>

<span data-ttu-id="0eb08-115">La fonctionnalité de télémétrie des outils .NET Core est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="0eb08-115">The .NET Core Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="0eb08-116">Vous pouvez ne pas adhérer à la fonctionnalité de télémétrie en définissant une variable d’environnement DOTNET_CLI_TELEMETRY_OPTOUT (par exemple, `export` sous Linux/Mac OS, `set` sur Windows) sur True (par exemple, « true », 1).</span><span class="sxs-lookup"><span data-stu-id="0eb08-116">You can opt-out of the telemetry feature by setting an environment variable DOTNET_CLI_TELEMETRY_OPTOUT (for example, `export` on macOS/Linux, `set` on Windows) to true (for example, "true", 1).</span></span>

## <a name="data-points"></a><span data-ttu-id="0eb08-117">Points de données</span><span class="sxs-lookup"><span data-stu-id="0eb08-117">Data Points</span></span>

<span data-ttu-id="0eb08-118">La fonctionnalité recueille les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="0eb08-118">The feature collects the following pieces of data:</span></span>

- <span data-ttu-id="0eb08-119">La commande utilisée (par exemple, « build », « restore »)</span><span class="sxs-lookup"><span data-stu-id="0eb08-119">The command being used (for example, "build", "restore")</span></span>
- <span data-ttu-id="0eb08-120">L’ExitCode de la commande</span><span class="sxs-lookup"><span data-stu-id="0eb08-120">The ExitCode of the command</span></span>
- <span data-ttu-id="0eb08-121">Pour les projets de test, le Test Runner utilisé</span><span class="sxs-lookup"><span data-stu-id="0eb08-121">For test projects, the test runner being used</span></span>
- <span data-ttu-id="0eb08-122">L’horodatage de l’appel</span><span class="sxs-lookup"><span data-stu-id="0eb08-122">The timestamp of invocation</span></span>
- <span data-ttu-id="0eb08-123">Le framework utilisé</span><span class="sxs-lookup"><span data-stu-id="0eb08-123">The framework used</span></span>
- <span data-ttu-id="0eb08-124">Si des ID d’exécution se trouvent sous le nœud « Runtimes »</span><span class="sxs-lookup"><span data-stu-id="0eb08-124">Whether runtime IDs are present in the "runtimes" node</span></span>
- <span data-ttu-id="0eb08-125">La version CLI utilisée</span><span class="sxs-lookup"><span data-stu-id="0eb08-125">The CLI version being used</span></span>

<span data-ttu-id="0eb08-126">La fonctionnalité ne collecte pas les informations personnelles, telles que les noms d’utilisateurs et les adresses e-mail.</span><span class="sxs-lookup"><span data-stu-id="0eb08-126">The feature will not collect any personal data, such as usernames or emails.</span></span> <span data-ttu-id="0eb08-127">Elle n’analyse pas votre code et n’extrait pas de données relatives au projet qui peuvent être considérées comme sensibles, telles que le nom, le dépôt ou l’auteur (si ceux-ci ont été définis dans votre project.json).</span><span class="sxs-lookup"><span data-stu-id="0eb08-127">It will not scan your code and not extract any project-level data that can be considered sensitive, such as name, repo or author (if you set those in your project.json).</span></span> <span data-ttu-id="0eb08-128">Nous souhaitons savoir comment vous utilisez les outils, et non ce que vous créez avec les outils.</span><span class="sxs-lookup"><span data-stu-id="0eb08-128">We want to know how the tools are used, not what you are building with the tools.</span></span> <span data-ttu-id="0eb08-129">Si vous vous rendez compte que des données sensibles ont été collectées, il s’agit d’un bogue.</span><span class="sxs-lookup"><span data-stu-id="0eb08-129">If you find sensitive data being collected, that’s a bug.</span></span> <span data-ttu-id="0eb08-130">Dans ce cas, [signalez le problème](https://github.com/dotnet/cli/issues) pour que celui-ci soit résolu.</span><span class="sxs-lookup"><span data-stu-id="0eb08-130">Please [file an issue](https://github.com/dotnet/cli/issues) and it will be fixed.</span></span>

## <a name="license"></a><span data-ttu-id="0eb08-131">Licence</span><span class="sxs-lookup"><span data-stu-id="0eb08-131">License</span></span>

<span data-ttu-id="0eb08-132">La distribution Microsoft de .NET Core est concédée sous licence avec le [CLUF de la BIBLIOTHÈQUE .NET MICROSOFT](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="0eb08-132">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="0eb08-133">Celui-ci comprend la section « DATA » ci-dessous, qui permet d’activer la télémétrie.</span><span class="sxs-lookup"><span data-stu-id="0eb08-133">This includes the "DATA" section re-printed below, to enable telemetry.</span></span>

<span data-ttu-id="0eb08-134">Les [packages NuGet .NET](https://www.nuget.org/profiles/dotnetframework) utilisent la même licence, mais ne permettent pas la télémétrie (voir la section [Portée](#scope) ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="0eb08-134">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use this same license but do not enable telemetry (see [Scope](#scope) above).</span></span>

> 2. <span data-ttu-id="0eb08-135">DONNÉES.</span><span class="sxs-lookup"><span data-stu-id="0eb08-135">DATA.</span></span> <span data-ttu-id="0eb08-136">Le logiciel peut collecter des informations sur vous et votre utilisation du logiciel et les envoyer à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0eb08-136">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="0eb08-137">Microsoft peut utiliser ces informations pour améliorer ses produits et services.</span><span class="sxs-lookup"><span data-stu-id="0eb08-137">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="0eb08-138">Vous pouvez en savoir plus sur la collecte et l’utilisation des données dans la documentation d’aide et la déclaration de confidentialité http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="0eb08-138">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="0eb08-139">Votre utilisation du logiciel est considérée comme votre acceptation de ces pratiques.</span><span class="sxs-lookup"><span data-stu-id="0eb08-139">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="0eb08-140">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="0eb08-140">Disclosure</span></span>

<span data-ttu-id="0eb08-141">Les outils .NET Core affichent le texte suivant lorsque vous exécutez une commande pour la première fois (par exemple, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="0eb08-141">The .NET Core Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="0eb08-142">Lors de cette première exécution, Microsoft vous informe sur la collecte de données.</span><span class="sxs-lookup"><span data-stu-id="0eb08-142">This "first run" experience is how Microsoft notifies you about data collection.</span></span> <span data-ttu-id="0eb08-143">C’est à ce moment-là que votre cache NuGet est alimenté avec les bibliothèques du SDK .NET Core, ce qui vous évite d’avoir à recourir à NuGet.org (ou autres flux NuGet) pour obtenir ces bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="0eb08-143">This same experience also initially populates your NuGet cache with the libraries in the .NET Core SDK, avoiding requests to NuGet.org (or other NuGet feed) for these libraries.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

