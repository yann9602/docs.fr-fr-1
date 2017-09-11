---
title: "Interpolation de chaîne - C#"
description: "Apprenez comment l’interpolation de chaîne fonctionne dans C# 6"
keywords: ".NET, .NET Core, C#, chaîne"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: de8f77e44319731f87f00d227a5373a78bf40e32
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="string-interpolation-in-c"></a><span data-ttu-id="846e4-104">Interpolation de chaîne en C#</span><span class="sxs-lookup"><span data-stu-id="846e4-104">String Interpolation in C#</span></span> #

<span data-ttu-id="846e4-105">L’interpolation de chaîne est la façon dont les espaces réservés dans une chaîne sont remplacés par la valeur d’une variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="846e4-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="846e4-106">Avant C# 6, la façon de procéder était avec `System.String.Format`.</span><span class="sxs-lookup"><span data-stu-id="846e4-106">Before C# 6, the way to do this is with `System.String.Format`.</span></span> <span data-ttu-id="846e4-107">Cela fonctionnait correctement, mais comme des espaces réservés numérotés étaient utilisés, la lecture pouvait être plus difficile et lourde.</span><span class="sxs-lookup"><span data-stu-id="846e4-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="846e4-108">D’autres langages de programmation ont une interpolation de chaîne intégrée depuis un certain temps.</span><span class="sxs-lookup"><span data-stu-id="846e4-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="846e4-109">Par exemple, dans PHP :</span><span class="sxs-lookup"><span data-stu-id="846e4-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="846e4-110">Dans C# 6, nous avons enfin ce style d’interpolation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="846e4-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="846e4-111">Vous pouvez utiliser un `$` avant une chaîne pour indiquer qu’elle doit remplacer les variables/expressions par leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="846e4-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="846e4-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="846e4-112">Prerequisites</span></span>
<span data-ttu-id="846e4-113">Vous devez configurer votre ordinateur pour exécuter .NET core.</span><span class="sxs-lookup"><span data-stu-id="846e4-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="846e4-114">Vous trouverez les instructions d’installation sur la page de [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="846e4-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="846e4-115">Vous pouvez exécuter cette application sur Windows, Ubuntu Linux, Mac OS ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="846e4-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="846e4-116">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="846e4-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="846e4-117">Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), un éditeur open source et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="846e4-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="846e4-118">Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.</span><span class="sxs-lookup"><span data-stu-id="846e4-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="846e4-119">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="846e4-119">Create the Application</span></span>

<span data-ttu-id="846e4-120">Maintenant que vous avez installé tous les outils, créez une nouvelle application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="846e4-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="846e4-121">Pour utiliser le générateur de ligne de commande, créez un répertoire pour votre projet, comme `interpolated`, et exécutez la commande suivante dans votre interpréteur de commandes préféré :</span><span class="sxs-lookup"><span data-stu-id="846e4-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="846e4-122">Cette commande crée un fichier projet, un projet de .NET Core simple, *interpolated.csproj* et un fichier de code source, *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="846e4-122">This command will create a barebones .NET core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="846e4-123">Vous devez exécuter `dotnet restore` pour restaurer les dépendances nécessaires à la compilation de ce projet.</span><span class="sxs-lookup"><span data-stu-id="846e4-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

<span data-ttu-id="846e4-124">Pour exécuter le programme, utilisez `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="846e4-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="846e4-125">Vous devriez voir le résultat dans la « Hello, World » dans la console.</span><span class="sxs-lookup"><span data-stu-id="846e4-125">You should see "Hello, World" output to the console.</span></span>

## <a name="intro-to-string-interpolation"></a><span data-ttu-id="846e4-126">Présentation de l’interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="846e4-126">Intro to String Interpolation</span></span>

<span data-ttu-id="846e4-127">Avec `System.String.Format`, vous spécifiez les « espaces réservés » dans une chaîne qui sont remplacés par les paramètres qui suivent cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="846e4-127">With `System.String.Format`, you specify "placeholders" in a string that are replaced by the parameters following the string.</span></span> <span data-ttu-id="846e4-128">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="846e4-128">For instance:</span></span>

<span data-ttu-id="846e4-129">[!code-csharp[Exemple de String.Format](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]</span><span class="sxs-lookup"><span data-stu-id="846e4-129">[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]</span></span>  

<span data-ttu-id="846e4-130">Cela générera « My name is Matt Groves ».</span><span class="sxs-lookup"><span data-stu-id="846e4-130">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="846e4-131">Dans C# 6, au lieu d’utiliser `String.Format`, vous définissez une chaîne interpolée en ajoutant le symbole `$` au début, puis en utilisant les variables directement dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="846e4-131">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="846e4-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="846e4-132">For instance:</span></span>

<span data-ttu-id="846e4-133">[!code-csharp[Exemple d’interpolation](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]</span><span class="sxs-lookup"><span data-stu-id="846e4-133">[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]</span></span>  

<span data-ttu-id="846e4-134">Vous n'êtes pas obligé d'utiliser seulement des variables.</span><span class="sxs-lookup"><span data-stu-id="846e4-134">You don't have to use just variables.</span></span> <span data-ttu-id="846e4-135">Vous pouvez utiliser n’importe quelle expression entre crochets.</span><span class="sxs-lookup"><span data-stu-id="846e4-135">You can use any expression within the brackets.</span></span> <span data-ttu-id="846e4-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="846e4-136">For instance:</span></span>

<span data-ttu-id="846e4-137">[!code-csharp[Exemple d’expression interpolation](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]</span><span class="sxs-lookup"><span data-stu-id="846e4-137">[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]</span></span>  

<span data-ttu-id="846e4-138">Ce qui devrait produire :</span><span class="sxs-lookup"><span data-stu-id="846e4-138">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="846e4-139">Fonctionnement de l’interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="846e4-139">How string interpolation works</span></span>

<span data-ttu-id="846e4-140">En arrière-plan, cette syntaxe d’interpolation de chaîne est convertie en String.Format par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="846e4-140">Behind the scenes, this string interpolation syntax is translated into String.Format by the compiler.</span></span> <span data-ttu-id="846e4-141">Par conséquent, vous pouvez faire [les mêmes choses qu’avec String.Format auparavant](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="846e4-141">So, you can do the [same type of stuff you've done before with String.Format](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).</span></span>

<span data-ttu-id="846e4-142">Par exemple, vous pouvez ajouter le remplissage et la mise en forme des nombres :</span><span class="sxs-lookup"><span data-stu-id="846e4-142">For instance, you can add padding and numeric formatting:</span></span>

<span data-ttu-id="846e4-143">[!code-csharp[Exemple de mise en forme d’interpolation](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]</span><span class="sxs-lookup"><span data-stu-id="846e4-143">[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]</span></span>  

<span data-ttu-id="846e4-144">La commande ci-dessus affiche quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="846e4-144">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="846e4-145">Si un nom de variable est introuvable, une erreur de compilation est générée.</span><span class="sxs-lookup"><span data-stu-id="846e4-145">If a variable name is not found, then a compile time error will be generated.</span></span>

<span data-ttu-id="846e4-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="846e4-146">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="846e4-147">Si vous compilez ce code, vous obtiendrez des erreurs :</span><span class="sxs-lookup"><span data-stu-id="846e4-147">If you compile this, you'll get errors:</span></span>
 
* <span data-ttu-id="846e4-148">`Cannot use local variable 'adj' before it is declared` - la variable `adj` n’a été déclarée *qu’après* la chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="846e4-148">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="846e4-149">`The name 'otheranimal' does not exist in the current context` - une variable appelée `otheranimal` n’a même pas été déclarée du tout</span><span class="sxs-lookup"><span data-stu-id="846e4-149">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="846e4-150">Localisation et internationalisation</span><span class="sxs-lookup"><span data-stu-id="846e4-150">Localization and Internationalization</span></span>

<span data-ttu-id="846e4-151">Une chaîne interpolée prend en charge `IFormattable` et `FormattableString`, ce qui peut être utile pour l’internationalisation.</span><span class="sxs-lookup"><span data-stu-id="846e4-151">An interpolated string supports `IFormattable` and `FormattableString`, which can be useful for internationalization.</span></span>

<span data-ttu-id="846e4-152">Par défaut, une chaîne interpolée utilise la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="846e4-152">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="846e4-153">Pour utiliser une autre culture, vous pouvez effectuer un cast en tant que `IFormattable`</span><span class="sxs-lookup"><span data-stu-id="846e4-153">To use a different culture, you could cast it as `IFormattable`</span></span>

<span data-ttu-id="846e4-154">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="846e4-154">For instance:</span></span>

<span data-ttu-id="846e4-155">[!code-csharp[Exemple d’internationalisation d’interpolation](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]</span><span class="sxs-lookup"><span data-stu-id="846e4-155">[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]</span></span>  

## <a name="conclusion"></a><span data-ttu-id="846e4-156">Conclusion</span><span class="sxs-lookup"><span data-stu-id="846e4-156">Conclusion</span></span> 

<span data-ttu-id="846e4-157">Dans ce didacticiel, vous avez appris comment utiliser les fonctionnalités d’interpolation des chaînes C# 6.</span><span class="sxs-lookup"><span data-stu-id="846e4-157">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="846e4-158">Il s’agit d’un moyen plus concis que l’écriture d’instructions `String.Format` simples, avec certains avertissements à garder à l’esprit pour des utilisations plus avancées.</span><span class="sxs-lookup"><span data-stu-id="846e4-158">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses of it.</span></span>

