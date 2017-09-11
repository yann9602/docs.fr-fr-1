---
title: "Catalogue d’identificateurs de runtime (RID) .NET Core"
description: "Découvrez plus en détails l’identificateur de runtime (RID) et la façon dont les identificateurs RID sont utilisés dans .NET Core."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3490fb639efd223dc36190324bdf3a06bc23c10e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a><span data-ttu-id="613c1-104">Catalogue d’identificateurs de runtime (RID) .NET Core</span><span class="sxs-lookup"><span data-stu-id="613c1-104">.NET Core Runtime IDentifier (RID) catalog</span></span>

## <a name="what-are-rids"></a><span data-ttu-id="613c1-105">En quoi consistent les RID ?</span><span class="sxs-lookup"><span data-stu-id="613c1-105">What are RIDs?</span></span>
<span data-ttu-id="613c1-106">RID est l’abréviation de *Runtime IDentifier* (identificateur de runtime).</span><span class="sxs-lookup"><span data-stu-id="613c1-106">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="613c1-107">Les RID servent à identifier les systèmes d’exploitation cibles sur lesquels une application ou une ressource (c’est-à-dire, un assembly) est appelée à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="613c1-107">RIDs are used to identify target operating systems where an application or asset (that is, assembly) will run.</span></span> <span data-ttu-id="613c1-108">Il se présentent de la façon suivante : « ubuntu.14.04-x64 », « win7-x64 », « osx.10.11-x64 ».</span><span class="sxs-lookup"><span data-stu-id="613c1-108">They look like this: "ubuntu.14.04-x64", "win7-x64", "osx.10.11-x64".</span></span> <span data-ttu-id="613c1-109">Pour les packages ayant des dépendances natives, les RID désignent les plateformes sur lesquelles ils peuvent être restaurés.</span><span class="sxs-lookup"><span data-stu-id="613c1-109">For the packages with native dependencies, it will designate on which platforms the package can be restored.</span></span> 

<span data-ttu-id="613c1-110">Il est important de noter que les RID sont des chaînes absolument opaques.</span><span class="sxs-lookup"><span data-stu-id="613c1-110">It is important to note that RIDs are really opaque strings.</span></span> <span data-ttu-id="613c1-111">Cela signifie qu’ils doivent correspondre exactement pour les opérations qui en ont besoin pour fonctionner.</span><span class="sxs-lookup"><span data-stu-id="613c1-111">This means that they have to match exactly for operations using them to work.</span></span> <span data-ttu-id="613c1-112">Par exemple, prenons le cas d’[Elementary OS](https://elementary.io/), qui est un clone simple d’Ubuntu 14.04.</span><span class="sxs-lookup"><span data-stu-id="613c1-112">As an example, let us consider the case of [Elementary OS](https://elementary.io/), which is a straightforward clone of Ubuntu 14.04.</span></span> <span data-ttu-id="613c1-113">Même si .NET Core et l’interface CLI fonctionnent par-dessus cette version d’Ubuntu, si vous essayez de les utiliser sur Elementary OS sans aucune modification, l’opération de restauration échoue pour n’importe quel package.</span><span class="sxs-lookup"><span data-stu-id="613c1-113">Although .NET Core and CLI work on top of that version of Ubuntu, if you try to use them on Elementary OS without any modifications, the restore operation for any package will fail.</span></span> <span data-ttu-id="613c1-114">Cela est dû au fait qu’il n’existe pas actuellement de RID pour désigner Elementary OS en tant que plateforme.</span><span class="sxs-lookup"><span data-stu-id="613c1-114">This is because we currently don't have a RID that designates Elementary OS as a platform.</span></span> 

<span data-ttu-id="613c1-115">Les RID qui représentent des systèmes d’exploitation concrets suivent généralement ce modèle : `[os].[version]-[arch]` où :</span><span class="sxs-lookup"><span data-stu-id="613c1-115">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[arch]` where:</span></span>
- <span data-ttu-id="613c1-116">`[os]` représente le moniker du système d’exploitation, par exemple, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="613c1-116">`[os]` is the operating system moniker, for example, `ubuntu`.</span></span>
- <span data-ttu-id="613c1-117">`[version]` représente le numéro de version du système d’exploitation séparé par un point (`.`), par exemple, `15.10`, suffisamment précis pour permettre raisonnablement aux ressources de cibler les API de la plateforme du système d’exploitation que cette version représente.</span><span class="sxs-lookup"><span data-stu-id="613c1-117">`[version]` is the operating system version in the form of a dot (`.`) separated version number, for example, `15.10`, accurate enough to reasonably enable assets to target operating system platform APIs represented by that version.</span></span>
  - <span data-ttu-id="613c1-118">Il **ne doit pas** s’agir de versions marketing, car celles-ci représentent souvent plusieurs versions distinctes du système d’exploitation avec une surface d’exposition variable des API de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="613c1-118">This **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>
- <span data-ttu-id="613c1-119">`[arch]` représente l’architecture du processeur, par exemple, `x86`, `x64`, `arm`, `arm64`, etc.</span><span class="sxs-lookup"><span data-stu-id="613c1-119">`[arch]` is the processor architecture, for example, `x86`, `x64`, `arm`, `arm64`, etc.</span></span>

<span data-ttu-id="613c1-120">Le graphique RID est défini dans un package appelé `Microsoft.NETCore.Platforms` dans un fichier appelé `runtime.json`, que vous pouvez trouver dans le [dépôt CoreFX](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span><span class="sxs-lookup"><span data-stu-id="613c1-120">The RID graph is defined in a package called `Microsoft.NETCore.Platforms` in a file called `runtime.json`, which you can see on the [CoreFX repo](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span></span> <span data-ttu-id="613c1-121">Si vous utilisez ce fichier, vous remarquerez que certains RID contiennent une instruction `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="613c1-121">If you use this file, you will notice that some of the RIDs have an `"#import"` statement in them.</span></span> <span data-ttu-id="613c1-122">Il s’agit d’une instruction de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="613c1-122">These statements are compatibility statements.</span></span> <span data-ttu-id="613c1-123">Autrement dit, un RID qui contient un RID importé peut être une cible pour la restauration de packages pour ce RID.</span><span class="sxs-lookup"><span data-stu-id="613c1-123">That means that a RID that has an imported RID in it can be a target for restoring packages for that RID.</span></span> <span data-ttu-id="613c1-124">Un peu déroutant, mais appuyons-nous sur un exemple</span><span class="sxs-lookup"><span data-stu-id="613c1-124">Slightly confusing, but let's look at an example.</span></span> <span data-ttu-id="613c1-125">(macOS) pour mieux comprendre :</span><span class="sxs-lookup"><span data-stu-id="613c1-125">Let's take a look at macOS:</span></span>

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
<span data-ttu-id="613c1-126">Le RID ci-dessus indique que `osx.10.11-x64` importe `osx.10.10-x64`.</span><span class="sxs-lookup"><span data-stu-id="613c1-126">The above RID specifies that `osx.10.11-x64` imports `osx.10.10-x64`.</span></span> <span data-ttu-id="613c1-127">Cela signifie qu’à l’occasion d’une restauration de packages, NuGet peut restaurer les packages qui indiquent avoir besoin de `osx.10.10-x64` sur `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="613c1-127">This means that when restoring packages, NuGet will be able to restore packages that specify that they need `osx.10.10-x64` on `osx.10.11-x64`.</span></span>

<span data-ttu-id="613c1-128">Voici un exemple de graphique RID légèrement plus complet :</span><span class="sxs-lookup"><span data-stu-id="613c1-128">A slightly bigger example RID graph:</span></span>  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

<span data-ttu-id="613c1-129">Tous les RID sont finalement remappés au RID `any` racine.</span><span class="sxs-lookup"><span data-stu-id="613c1-129">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="613c1-130">Même si leur utilisation paraît assez simple, les RID ont certaines caractéristiques particulières dont vous devez vous rappeler quand vous en utilisez :</span><span class="sxs-lookup"><span data-stu-id="613c1-130">Although they look easy enough to use, there are some special things about RIDs that you have to keep in mind when working with them:</span></span>

* <span data-ttu-id="613c1-131">Ce sont des **chaînes opaques** qui doivent être considérées comme des boîtes noires.</span><span class="sxs-lookup"><span data-stu-id="613c1-131">They are **opaque strings** and should be treated as black boxes</span></span>
    * <span data-ttu-id="613c1-132">Vous ne devez pas construire de RID par programmation.</span><span class="sxs-lookup"><span data-stu-id="613c1-132">You should not construct RIDs programmatically</span></span>
* <span data-ttu-id="613c1-133">Vous devez utiliser les RID qui sont déjà définis pour la plateforme, ce qui est illustré dans ce document.</span><span class="sxs-lookup"><span data-stu-id="613c1-133">You need to use the RIDs that are already defined for the platform and this document shows that</span></span>
* <span data-ttu-id="613c1-134">Les RID se devant d’être spécifiques, ne déduisez rien de leur valeur réelle. Consultez ce document pour identifier le ou les RID dont vous avez besoin pour une plateforme donnée.</span><span class="sxs-lookup"><span data-stu-id="613c1-134">The RIDs do need to be specific so don't assume anything from the actual RID value; please consult this document to determine which RID(s) you need for a given platform</span></span>

## <a name="using-rids"></a><span data-ttu-id="613c1-135">Utilisation de RID</span><span class="sxs-lookup"><span data-stu-id="613c1-135">Using RIDs</span></span>
<span data-ttu-id="613c1-136">Pour utiliser des RID, vous devez savoir à quoi ils correspondent.</span><span class="sxs-lookup"><span data-stu-id="613c1-136">In order to use RIDs, you have to know which RIDs there are.</span></span> <span data-ttu-id="613c1-137">De nouveaux RID sont régulièrement ajoutés à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="613c1-137">New RIDs are added regularly to the platform.</span></span> <span data-ttu-id="613c1-138">Pour en connaître la version la plus récente, consultez le fichier [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) dans le dépôt CoreFX.</span><span class="sxs-lookup"><span data-stu-id="613c1-138">For the latest version, please check the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

> [!NOTE]
> <span data-ttu-id="613c1-139">Nous œuvrons actuellement pour rendre ces informations plus interactives.</span><span class="sxs-lookup"><span data-stu-id="613c1-139">We are working towards getting this information into a more interactive form.</span></span> <span data-ttu-id="613c1-140">Cette page sera alors mise à jour et pointera vers cet outil et/ou sa documentation.</span><span class="sxs-lookup"><span data-stu-id="613c1-140">When that happens, this page will be updated to point to that tool and/or its usage documentation.</span></span> 

## <a name="windows-rids"></a><span data-ttu-id="613c1-141">RID Windows</span><span class="sxs-lookup"><span data-stu-id="613c1-141">Windows RIDs</span></span>

* <span data-ttu-id="613c1-142">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="613c1-142">Windows 7 / Windows Server 2008 R2</span></span>
    * `win7-x64`
    * `win7-x86`
* <span data-ttu-id="613c1-143">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="613c1-143">Windows 8 / Windows Server 2012</span></span>
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* <span data-ttu-id="613c1-144">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="613c1-144">Windows 8.1 / Windows Server 2012 R2</span></span>
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* <span data-ttu-id="613c1-145">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="613c1-145">Windows 10 / Windows Server 2016</span></span>
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a><span data-ttu-id="613c1-146">RID Linux</span><span class="sxs-lookup"><span data-stu-id="613c1-146">Linux RIDs</span></span>

* <span data-ttu-id="613c1-147">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="613c1-147">Red Hat Enterprise Linux</span></span>
    * `rhel.7-x64`
* <span data-ttu-id="613c1-148">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="613c1-148">Ubuntu</span></span>
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* <span data-ttu-id="613c1-149">CentOS</span><span class="sxs-lookup"><span data-stu-id="613c1-149">CentOS</span></span>
    * `centos.7-x64`
* <span data-ttu-id="613c1-150">Debian</span><span class="sxs-lookup"><span data-stu-id="613c1-150">Debian</span></span>
    * `debian.8-x64`
* <span data-ttu-id="613c1-151">Fedora</span><span class="sxs-lookup"><span data-stu-id="613c1-151">Fedora</span></span>
    * `fedora.23-x64`
    * `fedora.24-x64`
* <span data-ttu-id="613c1-152">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="613c1-152">OpenSUSE</span></span>
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* <span data-ttu-id="613c1-153">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="613c1-153">Oracle Linux</span></span>
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* <span data-ttu-id="613c1-154">Dérivés d’Ubuntu actuellement pris en charge</span><span class="sxs-lookup"><span data-stu-id="613c1-154">Currently supported Ubuntu derivatives</span></span> 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a><span data-ttu-id="613c1-155">RID OS X</span><span class="sxs-lookup"><span data-stu-id="613c1-155">OS X RIDs</span></span>

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

