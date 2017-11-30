---
title: "Quelles sont les nouveautés dans .NET Standard"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="3ec60-102">Quelles sont les nouveautés dans .NET Standard</span><span class="sxs-lookup"><span data-stu-id="3ec60-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="3ec60-103">.NET Standard est une spécification formelle qui définit un contrôle de version du jeu d’API qui doit être disponibles sur les implémentations de .NET qui sont conformes avec cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="3ec60-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3ec60-104">.NET Standard est destiné aux développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="3ec60-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3ec60-105">Une bibliothèque qui cible une version .NET Standard peut être utilisée sur toute implémentation du .NET Framework ou .NET Core Xamarin qui prend en charge cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="3ec60-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="3ec60-106">La version la plus récente de .NET Standard est 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ec60-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="3ec60-107">Il est inclus avec le Kit de développement logiciel .NET Core 2.0, ainsi qu’avec Visual Studio 2017 Version 15.3 avec la charge de travail .NET Core installé.</span><span class="sxs-lookup"><span data-stu-id="3ec60-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="3ec60-108">Implémentations .NET pris en charge</span><span class="sxs-lookup"><span data-stu-id="3ec60-108">Supported .NET implementations</span></span>

<span data-ttu-id="3ec60-109">La norme de .NET 2.0 est pris en charge par les implémentations .NET suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ec60-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="3ec60-110">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3ec60-110">.NET Core 2.0</span></span>
- <span data-ttu-id="3ec60-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3ec60-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="3ec60-112">Mono 5.4</span><span class="sxs-lookup"><span data-stu-id="3ec60-112">Mono 5.4</span></span>
- <span data-ttu-id="3ec60-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="3ec60-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="3ec60-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="3ec60-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="3ec60-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="3ec60-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="3ec60-116">Universal Windows Platform 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="3ec60-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="3ec60-117">Nouveautés de .NET 2.0 Standard</span><span class="sxs-lookup"><span data-stu-id="3ec60-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="3ec60-118">La norme de .NET 2.0 inclut les nouvelles fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ec60-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="3ec60-119">**Un jeu largement étendu d’API**</span><span class="sxs-lookup"><span data-stu-id="3ec60-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="3ec60-120">Jusqu'à la version 1.6, .NET Standard inclus un relativement petit sous-ensemble d’API.</span><span class="sxs-lookup"><span data-stu-id="3ec60-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="3ec60-121">Parmi ceux exclus ont de nombreuses API ont été utilisés dans le .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="3ec60-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="3ec60-122">Cela complique le développement, car elle requiert aux développeurs de trouver remplacements appropriés pour les API familier lorsqu’ils développent des applications et les bibliothèques qui ciblent plusieurs implémentations de .NET.</span><span class="sxs-lookup"><span data-stu-id="3ec60-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="3ec60-123">La norme de .NET 2.0 résout cette limitation en ajoutant plus de 20 000 API plus que dans la version 1.6 .NET Standard, la version précédente de la norme.</span><span class="sxs-lookup"><span data-stu-id="3ec60-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="3ec60-124">Pour obtenir la liste des API qui ont été ajoutés à la norme de .NET 2.0, consultez [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="3ec60-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="3ec60-125">Certains des ajouts à la <xref:System> inclure de l’espace de noms Standard de .NET 2.0 :</span><span class="sxs-lookup"><span data-stu-id="3ec60-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="3ec60-126">Prise en charge pour la <xref:System.AppDomain> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="3ec60-127">Meilleure prise en charge pour l’utilisation des groupes de membres supplémentaires dans la <xref:System.Array> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="3ec60-128">Meilleure prise en charge pour l’utilisation des attributs de membres supplémentaires dans la <xref:System.Attribute> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="3ec60-129">Calendrier mieux la prise en charge et les options de mise en forme supplémentaires pour <xref:System.DateTime> valeurs.</span><span class="sxs-lookup"><span data-stu-id="3ec60-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="3ec60-130">Supplémentaires <xref:System.Decimal> arrondi des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3ec60-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="3ec60-131">Des fonctionnalités supplémentaires dans la <xref:System.Environment> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="3ec60-132">Meilleur contrôle sur le garbage collector via la <xref:System.GC> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="3ec60-133">Meilleure prise en charge pour la comparaison de chaînes, énumération et la normalisation dans la <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="3ec60-134">Prise en charge de l’heure d’été réglages et les temps de transition dans le <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime> classes.</span><span class="sxs-lookup"><span data-stu-id="3ec60-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="3ec60-135">Considérablement améliorée des fonctionnalités dans le <xref:System.Type> classe.</span><span class="sxs-lookup"><span data-stu-id="3ec60-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="3ec60-136">Meilleure prise en charge pour la désérialisation des objets d’exception en ajoutant un constructeur d’exception avec <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext> paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ec60-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="3ec60-137">**Prise en charge pour les bibliothèques .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="3ec60-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="3ec60-138">La grande majorité des bibliothèques de cibler le .NET Framework plutôt que .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3ec60-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="3ec60-139">Toutefois, la plupart des appels dans ces bibliothèques est les API qui sont incluses dans la norme de .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ec60-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="3ec60-140">À compter de la norme de .NET 2.0, vous pouvez accéder à des bibliothèques de .NET Framework à partir d’une bibliothèque .NET Standard à l’aide un [shim de compatibilité](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="3ec60-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="3ec60-141">Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ec60-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="3ec60-142">La seule exigence est que les API appelées par la bibliothèque de classes .NET Framework doivent être inclus dans la norme de .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ec60-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="3ec60-143">**Prise en charge de Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="3ec60-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="3ec60-144">Vous pouvez maintenant développer les bibliothèques .NET Standard dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3ec60-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="3ec60-145">Pour les développeurs Visual Basic à l’aide de Visual Studio 2017 Version 15.3 ou version ultérieure avec la charge de travail .NET Core installé, Visual Studio inclut désormais un modèle de bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3ec60-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="3ec60-146">Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et les environnements, vous pouvez utiliser la [dotnet nouvelle](../../core/tools/dotnet-new.md) commande pour créer un projet de bibliothèque Standard de .NET.</span><span class="sxs-lookup"><span data-stu-id="3ec60-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="3ec60-147">Pour plus d’informations, consultez la [prise en charge pour les bibliothèques .NET Standard pour les outils](#tooling).</span><span class="sxs-lookup"><span data-stu-id="3ec60-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="3ec60-148"><a name="tooling" />**Prise en charge des outils pour les bibliothèques .NET Standard**</span><span class="sxs-lookup"><span data-stu-id="3ec60-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="3ec60-149">Avec la version de .NET Core 2.0 et .NET Standard 2.0, les deux 2017 Studio Visual et [.NET Core Interface de ligne de commande (CLI)](../../core/tools/index.md) incluent des outils de prise en charge pour la création de bibliothèques .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3ec60-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="3ec60-150">Si vous installez Visual Studio avec le **.NET Core le développement multiplateforme** charge de travail, vous pouvez créer un projet de bibliothèque Standard de .NET 2.0 à l’aide d’un modèle de projet, comme le montre l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="3ec60-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="3ec60-151">C#</span><span class="sxs-lookup"><span data-stu-id="3ec60-151">C#</span></span>](#tab/csharp)
![Ajouter le projet de bibliothèque de nouveau .NET Standard](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="3ec60-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ec60-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Ajouter le projet de bibliothèque de nouveau .NET Standard](./media/std-project-vb.png)
---

<span data-ttu-id="3ec60-155">Si vous utilisez l’interface .NET Core CLI, ce qui suit [dotnet nouvelle](../../core/tools/dotnet-new.md) commande crée un projet de bibliothèque de classes qui cible .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ec60-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="3ec60-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ec60-156">See Also</span></span>
<span data-ttu-id="3ec60-157">[.NET standard](../net-standard.md)
[présentation .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="3ec60-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
