---
title: "Télémétrie des outils CLI .NET Core"
description: "Découvrez les fonctionnalités de télémétrie des outils .NET Core, qui collectent des informations d’utilisation à des fins d’analyse, les types de données collectées et comment désactiver la télémétrie."
keywords: ".NET,.NET Core,télémétrie"
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.workload:
- dotnetcore
ms.openlocfilehash: 9a78ec370fd53260f26a5d8c15707a5d611e458f
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="bebfd-104">Télémétrie des outils CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="bebfd-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="bebfd-105">Le [SDK .NET Core](index.md) inclut une [fonctionnalité de télémétrie](https://github.com/dotnet/cli/pull/2145) qui recueille des informations d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="bebfd-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="bebfd-106">Il est important pour l’équipe .NET de comprendre la façon dont les outils sont utilisés, afin de pouvoir les améliorer.</span><span class="sxs-lookup"><span data-stu-id="bebfd-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="bebfd-107">Pour plus d’informations, consultez les [enseignements tirés de la fonctionnalité de télémétrie du SDK .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="bebfd-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="bebfd-108">Les données collectées sont anonymes et publiées sous forme regroupée en vue d’être utilisées par Microsoft et la communauté, sous la [licence Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="bebfd-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="bebfd-109">Portée</span><span class="sxs-lookup"><span data-stu-id="bebfd-109">Scope</span></span>

<span data-ttu-id="bebfd-110">La commande `dotnet` permet de lancer des applications et l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bebfd-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="bebfd-111">La commande `dotnet` ne permet pas de collecter des données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="bebfd-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="bebfd-112">Les commandes de l’interface CLI .NET Core exécutées par la commande `dotnet` collectent les données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="bebfd-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="bebfd-113">La télémétrie *n’est pas activée* quand vous utilisez la commande `dotnet` sans commande attachée :</span><span class="sxs-lookup"><span data-stu-id="bebfd-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="bebfd-114">La télémétrie *est activée* quand vous utilisez les [commandes de l’interface CLI .NET Core](index.md), telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bebfd-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="bebfd-115">Comportement</span><span class="sxs-lookup"><span data-stu-id="bebfd-115">Behavior</span></span>

<span data-ttu-id="bebfd-116">La fonctionnalité de télémétrie de l’interface CLI .NET Core est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="bebfd-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="bebfd-117">Pour ne pas l’utiliser, définissez la variable d’environnement `DOTNET_CLI_TELEMETRY_OPTOUT` sur `1` ou `true`.</span><span class="sxs-lookup"><span data-stu-id="bebfd-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="bebfd-118">Points de données</span><span class="sxs-lookup"><span data-stu-id="bebfd-118">Data points</span></span>

<span data-ttu-id="bebfd-119">La fonctionnalité recueille les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="bebfd-119">The feature collects the following data:</span></span>

- <span data-ttu-id="bebfd-120">horodatage de l’appel&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="bebfd-121">Commande appelée (par exemple, « build »)&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="bebfd-122">Adresse IP de trois octets utilisée pour déterminer l’emplacement géographique&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="bebfd-123">`ExitCode` de la commande</span><span class="sxs-lookup"><span data-stu-id="bebfd-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="bebfd-124">Exécuteur de tests (pour les projets de test)</span><span class="sxs-lookup"><span data-stu-id="bebfd-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="bebfd-125">Système d’exploitation et version&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="bebfd-126">Si des ID d’exécution se trouvent sous le nœud runtimes</span><span class="sxs-lookup"><span data-stu-id="bebfd-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="bebfd-127">Version du SDK .NET Core&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="bebfd-128">&#8224;Cette métrique est publiée.</span><span class="sxs-lookup"><span data-stu-id="bebfd-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="bebfd-129">À compter du SDK .NET Core 2.0, de nouveaux points de données sont collectés :</span><span class="sxs-lookup"><span data-stu-id="bebfd-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="bebfd-130">Arguments et options de la commande `dotnet` : seuls les arguments et options connus sont collectés (pas les chaînes arbitraires).</span><span class="sxs-lookup"><span data-stu-id="bebfd-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="bebfd-131">Si le SDK est en cours d’exécution dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="bebfd-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="bebfd-132">Frameworks cibles.</span><span class="sxs-lookup"><span data-stu-id="bebfd-132">Target frameworks.</span></span>
- <span data-ttu-id="bebfd-133">Adresse MAC hachée : ID unique et anonyme chiffré (SHA256) pour une machine.</span><span class="sxs-lookup"><span data-stu-id="bebfd-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="bebfd-134">Cette métrique n’est pas publiée.</span><span class="sxs-lookup"><span data-stu-id="bebfd-134">This metric is not published.</span></span>
- <span data-ttu-id="bebfd-135">Répertoire de travail actuel haché.</span><span class="sxs-lookup"><span data-stu-id="bebfd-135">Hashed current working directory.</span></span>

<span data-ttu-id="bebfd-136">La fonctionnalité ne collecte pas les informations personnelles, telles que les noms d’utilisateurs et les adresses e-mail.</span><span class="sxs-lookup"><span data-stu-id="bebfd-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="bebfd-137">Elle n’analyse pas votre code et n’extrait pas de données sensibles au niveau du projet, telles que le nom, le dépôt ou l’auteur.</span><span class="sxs-lookup"><span data-stu-id="bebfd-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="bebfd-138">Les données sont envoyées en toute sécurité à des serveurs Microsoft à l’aide de la technologie [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), stockées à un emplacement dont l’accès est strictement limité et publiées conformément à des contrôles de sécurité stricts à partir de systèmes [Azure Storage](https://azure.microsoft.com/services/storage/) sécurisés.</span><span class="sxs-lookup"><span data-stu-id="bebfd-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="bebfd-139">Nous souhaitons savoir comment vous utilisez les outils et s’ils fonctionnent correctement, et non ce que vous créez avec les outils.</span><span class="sxs-lookup"><span data-stu-id="bebfd-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="bebfd-140">Si vous pensez que la fonctionnalité de télémétrie collecte des données sensibles ou que nous gérons des données de manière non sécurisée ou incorrecte, [soumettez un problème dans la page des problèmes du dépôt dotnet/cli](https://github.com/dotnet/cli/issues) afin que nous effectuions un examen plus approfondi.</span><span class="sxs-lookup"><span data-stu-id="bebfd-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="bebfd-141">Données publiées</span><span class="sxs-lookup"><span data-stu-id="bebfd-141">Published data</span></span>

<span data-ttu-id="bebfd-142">Les données publiées sont disponibles tous les trimestres et sont répertoriées dans la page [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Données d’utilisation du SDK .NET Core).</span><span class="sxs-lookup"><span data-stu-id="bebfd-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="bebfd-143">Les colonnes d’un fichier de données sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bebfd-143">The columns of a data file are:</span></span>
- <span data-ttu-id="bebfd-144">Horodateur</span><span class="sxs-lookup"><span data-stu-id="bebfd-144">Timestamp</span></span>
- <span data-ttu-id="bebfd-145">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="bebfd-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="bebfd-146">Commande</span><span class="sxs-lookup"><span data-stu-id="bebfd-146">Command</span></span>
- <span data-ttu-id="bebfd-147">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="bebfd-147">Geography&#8225;</span></span>
- <span data-ttu-id="bebfd-148">OSFamily</span><span class="sxs-lookup"><span data-stu-id="bebfd-148">OSFamily</span></span>
- <span data-ttu-id="bebfd-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="bebfd-149">RuntimeID</span></span>
- <span data-ttu-id="bebfd-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="bebfd-150">OSVersion</span></span>
- <span data-ttu-id="bebfd-151">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="bebfd-151">SDKVersion</span></span>

<span data-ttu-id="bebfd-152">&#8224;La colonne *Occurrences* totalise le nombre d’utilisations de la commande concernée pour les métriques de la ligne donnée le jour indiqué.</span><span class="sxs-lookup"><span data-stu-id="bebfd-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="bebfd-153">&#8225;En règle générale, la colonne *Geography* affiche le nom d’un pays.</span><span class="sxs-lookup"><span data-stu-id="bebfd-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="bebfd-154">Dans certains cas, le continent Antarctica (Antarctique) apparaît dans cette colonne si .NET Core est utilisé dans ce continent ou que les données de localisation sont incorrectes.</span><span class="sxs-lookup"><span data-stu-id="bebfd-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="bebfd-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="bebfd-155">Example</span></span>

| <span data-ttu-id="bebfd-156">Horodateur</span><span class="sxs-lookup"><span data-stu-id="bebfd-156">Timestamp</span></span>      | <span data-ttu-id="bebfd-157">Occurrences</span><span class="sxs-lookup"><span data-stu-id="bebfd-157">Occurrences</span></span> | <span data-ttu-id="bebfd-158">Commande</span><span class="sxs-lookup"><span data-stu-id="bebfd-158">Command</span></span> | <span data-ttu-id="bebfd-159">Geography</span><span class="sxs-lookup"><span data-stu-id="bebfd-159">Geography</span></span> | <span data-ttu-id="bebfd-160">OSFamily</span><span class="sxs-lookup"><span data-stu-id="bebfd-160">OSFamily</span></span> | <span data-ttu-id="bebfd-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="bebfd-161">RuntimeID</span></span>     | <span data-ttu-id="bebfd-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="bebfd-162">OSVersion</span></span> | <span data-ttu-id="bebfd-163">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="bebfd-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="bebfd-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="bebfd-164">4/16/2017 0:00</span></span> | <span data-ttu-id="bebfd-165">8</span><span class="sxs-lookup"><span data-stu-id="bebfd-165">8</span></span>           | <span data-ttu-id="bebfd-166">run</span><span class="sxs-lookup"><span data-stu-id="bebfd-166">run</span></span>     | <span data-ttu-id="bebfd-167">Uganda</span><span class="sxs-lookup"><span data-stu-id="bebfd-167">Uganda</span></span>    | <span data-ttu-id="bebfd-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="bebfd-168">Darwin</span></span>   | <span data-ttu-id="bebfd-169">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="bebfd-169">osx.10.12-x64</span></span> | <span data-ttu-id="bebfd-170">10.12</span><span class="sxs-lookup"><span data-stu-id="bebfd-170">10.12</span></span>     | <span data-ttu-id="bebfd-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="bebfd-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="bebfd-172">Groupes de données</span><span class="sxs-lookup"><span data-stu-id="bebfd-172">Datasets</span></span>

[<span data-ttu-id="bebfd-173">2016 - T3</span><span class="sxs-lookup"><span data-stu-id="bebfd-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="bebfd-174">2016 - T4</span><span class="sxs-lookup"><span data-stu-id="bebfd-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="bebfd-175">2017 - T1</span><span class="sxs-lookup"><span data-stu-id="bebfd-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="bebfd-176">2017 - T2</span><span class="sxs-lookup"><span data-stu-id="bebfd-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="bebfd-177">Des jeux de données supplémentaires sont publiés à l’aide d’un format d’URL standard.</span><span class="sxs-lookup"><span data-stu-id="bebfd-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="bebfd-178">Remplacez `<YEAR>` par l’année, et `<QUARTER>` par le trimestre de l’année (utilisez `1`, `2`, `3` ou `4`).</span><span class="sxs-lookup"><span data-stu-id="bebfd-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="bebfd-179">Les fichiers sont au format *TSV* (valeurs séparées par une tabulation).</span><span class="sxs-lookup"><span data-stu-id="bebfd-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="bebfd-180">Licence</span><span class="sxs-lookup"><span data-stu-id="bebfd-180">License</span></span>

<span data-ttu-id="bebfd-181">La distribution Microsoft de .NET Core est concédée sous licence avec le [CLUF de la BIBLIOTHÈQUE .NET MICROSOFT](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="bebfd-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="bebfd-182">Cette licence comprend la section « DATA » qui permet d’activer la télémétrie (ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="bebfd-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="bebfd-183">Les [packages NuGet .NET](https://www.nuget.org/profiles/dotnetframework) utilisent la même licence, mais ne permettent pas la télémétrie (voir la section [Portée](#scope)).</span><span class="sxs-lookup"><span data-stu-id="bebfd-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="bebfd-184">DONNÉES.</span><span class="sxs-lookup"><span data-stu-id="bebfd-184">DATA.</span></span> <span data-ttu-id="bebfd-185">Le logiciel peut collecter des informations sur vous et votre utilisation du logiciel et les envoyer à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bebfd-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="bebfd-186">Microsoft peut utiliser ces informations pour améliorer ses produits et services.</span><span class="sxs-lookup"><span data-stu-id="bebfd-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="bebfd-187">Vous pouvez en savoir plus sur la collecte et l’utilisation des données dans la documentation d’aide et la déclaration de confidentialité http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="bebfd-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="bebfd-188">Votre utilisation du logiciel est considérée comme votre acceptation de ces pratiques.</span><span class="sxs-lookup"><span data-stu-id="bebfd-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="bebfd-189">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="bebfd-189">Disclosure</span></span>

<span data-ttu-id="bebfd-190">Les outils CLI .NET Core affichent le texte suivant quand vous exécutez une commande pour la première fois (par exemple, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="bebfd-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="bebfd-191">Le texte peut varier légèrement selon la version du SDK que vous exécutez.</span><span class="sxs-lookup"><span data-stu-id="bebfd-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="bebfd-192">Lors de cette première exécution, Microsoft vous informe sur la collecte de données.</span><span class="sxs-lookup"><span data-stu-id="bebfd-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="bebfd-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bebfd-193">See also</span></span>

<span data-ttu-id="bebfd-194">[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (Enseignements tirés de la fonctionnalité de télémétrie du SDK .NET Core)</span><span class="sxs-lookup"><span data-stu-id="bebfd-194">[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)</span></span>  
<span data-ttu-id="bebfd-195">[Source de référence de télémétrie (dotnet/cli repo ; branche release/2.0.0)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span><span class="sxs-lookup"><span data-stu-id="bebfd-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span></span>  
<span data-ttu-id="bebfd-196">[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Données d’utilisation du SDK .NET Core)</span><span class="sxs-lookup"><span data-stu-id="bebfd-196">[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)</span></span>
