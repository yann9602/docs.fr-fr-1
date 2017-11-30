---
title: "Quelles sont les nouveautés dans c# 7.1"
description: "Vue d’ensemble des nouvelles fonctionnalités de c# 7.1."
keywords: Conception du langage c#, 7.1, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="db576-104">Quelles sont les nouveautés dans c# 7.1</span><span class="sxs-lookup"><span data-stu-id="db576-104">What's new in C# 7.1</span></span>

<span data-ttu-id="db576-105">7.1 c# est la première version de point pour le langage c#.</span><span class="sxs-lookup"><span data-stu-id="db576-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="db576-106">Il marque une cadence de publication accrue pour la langue.</span><span class="sxs-lookup"><span data-stu-id="db576-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="db576-107">Vous pouvez utiliser les nouvelles fonctionnalités plus tôt, dans l’idéal, lorsque chaque nouvelle fonctionnalité est prête.</span><span class="sxs-lookup"><span data-stu-id="db576-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="db576-108">7.1 c# ajoute la possibilité de configurer le compilateur pour correspondre à une version spécifiée de la langue.</span><span class="sxs-lookup"><span data-stu-id="db576-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="db576-109">Qui vous permet de séparer la décision de mettre à niveau les outils à partir de la décision de mettre à niveau les versions de langue.</span><span class="sxs-lookup"><span data-stu-id="db576-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="db576-110">7.1 c# ajoute le [sélection de la version linguistique](#language-version-selection) élément de configuration, trois nouvelles fonctionnalités de langage et nouveau comportement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="db576-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="db576-111">Les nouvelles fonctionnalités de langage dans cette version sont :</span><span class="sxs-lookup"><span data-stu-id="db576-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="db576-112">`async``Main` (méthode)</span><span class="sxs-lookup"><span data-stu-id="db576-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="db576-113">Le point d’entrée pour une application peut avoir la `async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="db576-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="db576-114">`default`expressions littérales</span><span class="sxs-lookup"><span data-stu-id="db576-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="db576-115">Vous pouvez utiliser les expressions littérales par défaut dans les expressions de valeur par défaut lorsque le type de cible peut être déduit.</span><span class="sxs-lookup"><span data-stu-id="db576-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="db576-116">Noms d’élément de tuple déduit</span><span class="sxs-lookup"><span data-stu-id="db576-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="db576-117">Les noms d’éléments de tuple peuvent être déduits à partir de l’initialisation de tuple dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="db576-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="db576-118">Enfin, le compilateur a deux options `/refout` et `/refonly` ce contrôle [génération de l’assembly de référence](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="db576-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="db576-119">Sélection de la version linguistique</span><span class="sxs-lookup"><span data-stu-id="db576-119">Language version selection</span></span>

<span data-ttu-id="db576-120">Le compilateur Visual c# prend en charge c# 7.1 commençant par Visual Studio 2017 version 15.3 ou .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="db576-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="db576-121">Toutefois, les 7.1 fonctionnalités sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="db576-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="db576-122">Pour activer les 7.1 fonctionnalités, vous devez modifier le paramètre de version de langue de votre projet.</span><span class="sxs-lookup"><span data-stu-id="db576-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="db576-123">Dans Visual Studio, avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="db576-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="db576-124">Sélectionnez le **générer** onglet et sélectionnez le **avancé** bouton.</span><span class="sxs-lookup"><span data-stu-id="db576-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="db576-125">Dans la liste déroulante, sélectionnez **c# dernière version mineure (dernière version)**, ou la version spécifique **c# 7.1** comme indiqué dans l’exemple suivant d’image.</span><span class="sxs-lookup"><span data-stu-id="db576-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="db576-126">Le `latest` valeur signifie que vous souhaitez utiliser la dernière version mineure de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="db576-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="db576-127">Le `C# 7.1` signifie que vous souhaitez utiliser c# 7.1, même après le lancement des nouvelles versions mineures.</span><span class="sxs-lookup"><span data-stu-id="db576-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Définition de la version de langue](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="db576-129">Vous pouvez également modifier le fichier « csproj » et ajouter ou modifier les lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="db576-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="db576-130">Si vous utilisez l’IDE de Visual Studio pour mettre à jour vos fichiers csproj, l’interface IDE crée des nœuds distincts pour chaque configuration de build.</span><span class="sxs-lookup"><span data-stu-id="db576-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="db576-131">Vous devez généralement définir la valeur de la même dans toutes les configurations de build, mais vous devez définir explicitement pour chaque configuration de build, ou sélectionnez « Toutes les Configurations » lorsque vous modifiez ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="db576-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="db576-132">Vous verrez les éléments suivants dans votre fichier csproj :</span><span class="sxs-lookup"><span data-stu-id="db576-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="db576-133">Les paramètres appropriés pour le `LangVersion` élément sont :</span><span class="sxs-lookup"><span data-stu-id="db576-133">Valid settings for the `LangVersion` element are:</span></span>

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

<span data-ttu-id="db576-134">Les chaînes spéciales `default` et `latest` résoudre aux dernières versions majeure et mineure langue installées sur l’ordinateur de build, respectivement.</span><span class="sxs-lookup"><span data-stu-id="db576-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="db576-135">Ce paramètre dissocie l’installation de nouvelles versions des outils et Kit de développement logiciel dans votre environnement de développement de choisir d’incorporer les nouvelles fonctionnalités de langage dans un projet.</span><span class="sxs-lookup"><span data-stu-id="db576-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="db576-136">Vous pouvez installer les outils et Kit de développement logiciel plus récentes sur votre ordinateur de build.</span><span class="sxs-lookup"><span data-stu-id="db576-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="db576-137">Chaque projet peut être configuré pour utiliser une version spécifique de la langue pour sa génération.</span><span class="sxs-lookup"><span data-stu-id="db576-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="db576-138">Async principal</span><span class="sxs-lookup"><span data-stu-id="db576-138">Async main</span></span>

<span data-ttu-id="db576-139">Un *async principal* méthode vous permet d’utiliser `await` dans votre `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="db576-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="db576-140">Auparavant, vous deviez écrire :</span><span class="sxs-lookup"><span data-stu-id="db576-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="db576-141">Vous pouvez maintenant écrire :</span><span class="sxs-lookup"><span data-stu-id="db576-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="db576-142">Si votre programme ne renvoie pas un code de sortie, vous pouvez déclarer un `Main` méthode qui retourne un <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="db576-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="db576-143">Vous pouvez en savoir plus sur les détails dans le [async principal](../programming-guide/main-and-command-args/index.md) rubrique du guide de programmation.</span><span class="sxs-lookup"><span data-stu-id="db576-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="db576-144">Expressions littérales par défaut</span><span class="sxs-lookup"><span data-stu-id="db576-144">Default literal expressions</span></span>

<span data-ttu-id="db576-145">Les expressions littérales par défaut sont une amélioration aux expressions de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="db576-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="db576-146">Ces expressions initialisent une variable à la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="db576-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="db576-147">Dans lequel vous précédemment devez écrire :</span><span class="sxs-lookup"><span data-stu-id="db576-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="db576-148">Vous pouvez maintenant omettre le type sur le côté droit de l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="db576-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="db576-149">Vous pouvez en savoir plus sur cette fonctionnalité dans la rubrique du Guide de programmation c# sur [par défaut des expressions de valeur](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="db576-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="db576-150">Cette fonctionnalité modifie également parmi les règles d’analyse pour le [mot clé default](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="db576-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="db576-151">Noms d’élément de tuple déduit</span><span class="sxs-lookup"><span data-stu-id="db576-151">Inferred tuple element names</span></span>

<span data-ttu-id="db576-152">Cette fonctionnalité est une amélioration de petite à la fonctionnalité de tuples introduite dans c# 7.0.</span><span class="sxs-lookup"><span data-stu-id="db576-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="db576-153">Plusieurs fois lorsque vous initialisez un tuple, les variables utilisées pour le côté droit de l’affectation sont identiques à ceux que vous souhaitez que les éléments de tuple :</span><span class="sxs-lookup"><span data-stu-id="db576-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="db576-154">Les noms d’éléments de tuple peuvent être déduits à partir de variables utilisés pour initialiser le tuple dans c# 7.1 :</span><span class="sxs-lookup"><span data-stu-id="db576-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="db576-155">Plus d’informations sur cette fonctionnalité dans le [Tuples](../tuples.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="db576-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="db576-156">Génération d’assembly de référence</span><span class="sxs-lookup"><span data-stu-id="db576-156">Reference assembly generation</span></span>

<span data-ttu-id="db576-157">Il existe deux nouvelles options du compilateur qui génèrent des *les assemblys de référence uniquement*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) et [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="db576-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="db576-158">Les rubriques associées expliquent ces options et les assemblys de référence plus en détail.</span><span class="sxs-lookup"><span data-stu-id="db576-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
