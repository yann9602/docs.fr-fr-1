---
title: "Catalogue d’identificateurs de runtime (RID) .NET Core"
description: "Découvrez plus en détails l’identificateur de runtime (RID) et la façon dont les identificateurs RID sont utilisés dans .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="ad2f0-103">Catalogue RID .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad2f0-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="ad2f0-104">RID est l’abréviation de *Runtime IDentifier* (identificateur de runtime).</span><span class="sxs-lookup"><span data-stu-id="ad2f0-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="ad2f0-105">Les valeurs RID sont utilisées pour identifier les plateformes cibles où l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="ad2f0-106">Elles sont utilisées par les packages .NET pour représenter des ressources spécifiques à une plateforme dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="ad2f0-107">Les valeurs suivantes sont des exemples d’identificateurs RID : `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="ad2f0-108">Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="ad2f0-109">Les RID peuvent être définis dans l’élément `<RuntimeIdentifier>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="ad2f0-110">Ils sont également utilisés par le biais de l’option `--runtime` avec les [commandes de l’interface CLI .NET Core](./tools/index.md) suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad2f0-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="ad2f0-111">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ad2f0-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="ad2f0-112">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ad2f0-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="ad2f0-113">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ad2f0-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="ad2f0-114">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ad2f0-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="ad2f0-115">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ad2f0-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="ad2f0-116">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ad2f0-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="ad2f0-117">dotnet store</span><span class="sxs-lookup"><span data-stu-id="ad2f0-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="ad2f0-118">Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[architecture]-[additional qualifiers]` où :</span><span class="sxs-lookup"><span data-stu-id="ad2f0-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="ad2f0-119">`[os]` représente le moniker du système d’exploitation/de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="ad2f0-120">Par exemple, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="ad2f0-121">`[version]` représente la version du système d’exploitation sous la forme d’un numéro de version (`.`) séparé par un point.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="ad2f0-122">Par exemple, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="ad2f0-123">La version **ne doit pas** correspondre à des versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="ad2f0-124">`[architecture]` représente l’architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="ad2f0-125">Par exemple : `x86`, `x64`, `arm` ou `arm64`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="ad2f0-126">`[additional qualifiers]` permet de distinguer davantage les plateformes.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="ad2f0-127">Par exemple : `aot` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="ad2f0-128">Graphe RID</span><span class="sxs-lookup"><span data-stu-id="ad2f0-128">RID graph</span></span>

<span data-ttu-id="ad2f0-129">Le graphe RID ou le graphe de secours du runtime consiste en une liste d’identificateurs RID compatibles entre eux.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="ad2f0-130">Les RID sont définis dans le package [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="ad2f0-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="ad2f0-131">Vous pouvez consulter la liste des RID pris en charge et le graphe RID dans le fichier [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json), situé dans le référentiel CoreFX.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="ad2f0-132">Dans ce fichier, vous pouvez voir que tous les RID, sauf celui de base, contiennent une instruction `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="ad2f0-133">Ces instructions indiquent des RID compatibles.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="ad2f0-134">Lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour le runtime spécifié.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="ad2f0-135">Si aucune correspondance exacte n’est trouvée, NuGet remonte le graphe jusqu'à ce qu’il trouve le système compatible le plus proche selon le graphe RID.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="ad2f0-136">L’exemple suivant est l’entrée réelle pour le RID `osx.10.12-x64` :</span><span class="sxs-lookup"><span data-stu-id="ad2f0-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="ad2f0-137">Le RID ci-dessus indique que `osx.10.12-x64` importe `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="ad2f0-138">Donc, lorsque NuGet restaure des packages, il tente de trouver une correspondance exacte pour `osx.10.12-x64` dans le package.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="ad2f0-139">Si NuGet ne trouve pas le runtime spécifique, il peut restaurer des packages qui spécifient des runtimes `osx.10.11-x64`, par exemple.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="ad2f0-140">L’exemple suivant illustre un graphe RID légèrement plus grand également défini dans le fichier *runtime.json* :</span><span class="sxs-lookup"><span data-stu-id="ad2f0-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="ad2f0-141">Tous les RID sont finalement remappés au RID `any` racine.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="ad2f0-142">Lorsque vous utilisez les RID, il existe quelques remarques que vous devez garder à l’esprit :</span><span class="sxs-lookup"><span data-stu-id="ad2f0-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="ad2f0-143">Les RID sont des **chaînes opaques** qui doivent être considérées comme des boîtes noires.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="ad2f0-144">Ne générez pas les RID par programme.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="ad2f0-145">Utilisez des RID déjà définis pour la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="ad2f0-146">Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="ad2f0-147">Utilisation de RID</span><span class="sxs-lookup"><span data-stu-id="ad2f0-147">Using RIDs</span></span>

<span data-ttu-id="ad2f0-148">Pour utiliser des RID, vous devez savoir lesquels existent.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="ad2f0-149">De nouvelles valeurs sont régulièrement ajoutées à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="ad2f0-150">Pour en connaître la version complète la plus récente, consultez le fichier [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) dans le référentiel CoreFX.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="ad2f0-151">Le kit SDK .NET Core 2.0 introduit le concept d’identificateurs RID portables.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="ad2f0-152">Il s’agit de nouvelles valeurs ajoutées au graphe RID qui ne sont liées à aucune version ou distribution du système d’exploitation spécifique.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="ad2f0-153">Ils sont particulièrement utiles lors du traitement de plusieurs versions de Linux.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="ad2f0-154">La liste suivante présente les RID les plus courants utilisés pour chaque système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="ad2f0-155">Elle ne traite pas les valeurs `arm` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="ad2f0-156">RID Windows</span><span class="sxs-lookup"><span data-stu-id="ad2f0-156">Windows RIDs</span></span>

- <span data-ttu-id="ad2f0-157">Portable</span><span class="sxs-lookup"><span data-stu-id="ad2f0-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="ad2f0-158">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ad2f0-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="ad2f0-159">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ad2f0-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="ad2f0-160">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ad2f0-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="ad2f0-161">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ad2f0-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="ad2f0-162">Consultez [configuration requise pour .NET Core sur Windows](windows-prerequisites.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="ad2f0-163">RID Linux</span><span class="sxs-lookup"><span data-stu-id="ad2f0-163">Linux RIDs</span></span>

- <span data-ttu-id="ad2f0-164">Portable</span><span class="sxs-lookup"><span data-stu-id="ad2f0-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="ad2f0-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="ad2f0-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="ad2f0-166">Debian</span><span class="sxs-lookup"><span data-stu-id="ad2f0-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="ad2f0-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad2f0-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="ad2f0-168">`fedora.25-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="ad2f0-169">`fedora.26-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="ad2f0-170">Gentoo (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="ad2f0-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ad2f0-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="ad2f0-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ad2f0-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="ad2f0-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ad2f0-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="ad2f0-174">`rhel.6-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="ad2f0-175">`rhel.7.3-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="ad2f0-176">`rhel.7.4-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="ad2f0-177">Tizen (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="ad2f0-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad2f0-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="ad2f0-179">Dérivés d’Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad2f0-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="ad2f0-180">`linuxmint.18.1-x64` (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="ad2f0-181">Consultez [configuration requise pour .NET Core sur Linux](linux-prerequisites.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="ad2f0-182">macOS RID</span><span class="sxs-lookup"><span data-stu-id="ad2f0-182">macOS RIDs</span></span>

<span data-ttu-id="ad2f0-183">macOS RID utiliser la personnalisation de « OSX » plus anciens.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="ad2f0-184">`osx-x64`(.NET core 2.0 ou versions ultérieures, la version minimale est `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="ad2f0-185">`osx.10.12-x64` (.NET Core 1.1 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="ad2f0-186">Consultez [configuration requise pour .NET Core sur macOS](macos-prerequisites.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ad2f0-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="ad2f0-187">RID Android (.NET Core 2.0 ou versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="ad2f0-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="ad2f0-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad2f0-188">See also</span></span>

[<span data-ttu-id="ad2f0-189">ID du runtime</span><span class="sxs-lookup"><span data-stu-id="ad2f0-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
