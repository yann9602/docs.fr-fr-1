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
# <a name="whats-new-in-c-71"></a>Quelles sont les nouveautés dans c# 7.1

7.1 c# est la première version de point pour le langage c#. Il marque une cadence de publication accrue pour la langue. Vous pouvez utiliser les nouvelles fonctionnalités plus tôt, dans l’idéal, lorsque chaque nouvelle fonctionnalité est prête. 7.1 c# ajoute la possibilité de configurer le compilateur pour correspondre à une version spécifiée de la langue. Qui vous permet de séparer la décision de mettre à niveau les outils à partir de la décision de mettre à niveau les versions de langue.

7.1 c# ajoute le [sélection de la version linguistique](#language-version-selection) élément de configuration, trois nouvelles fonctionnalités de langage et nouveau comportement du compilateur.

Les nouvelles fonctionnalités de langage dans cette version sont :

* [`async``Main` (méthode)](#async-main)
  - Le point d’entrée pour une application peut avoir la `async` modificateur.
* [`default`expressions littérales](#default-literal-expressions)
  - Vous pouvez utiliser les expressions littérales par défaut dans les expressions de valeur par défaut lorsque le type de cible peut être déduit.
* [Noms d’élément de tuple déduit](#inferred-tuple-element-names)
  - Les noms d’éléments de tuple peuvent être déduits à partir de l’initialisation de tuple dans de nombreux cas.

Enfin, le compilateur a deux options `/refout` et `/refonly` ce contrôle [génération de l’assembly de référence](#reference-assembly-generation).

## <a name="language-version-selection"></a>Sélection de la version linguistique

Le compilateur Visual c# prend en charge c# 7.1 commençant par Visual Studio 2017 version 15.3 ou .NET Core SDK 2.0. Toutefois, les 7.1 fonctionnalités sont désactivées par défaut. Pour activer les 7.1 fonctionnalités, vous devez modifier le paramètre de version de langue de votre projet.

Dans Visual Studio, avec le bouton droit sur le nœud de projet dans l’Explorateur de solutions et sélectionnez **propriétés**. Sélectionnez le **générer** onglet et sélectionnez le **avancé** bouton. Dans la liste déroulante, sélectionnez **c# dernière version mineure (dernière version)**, ou la version spécifique **c# 7.1** comme indiqué dans l’exemple suivant d’image. Le `latest` valeur signifie que vous souhaitez utiliser la dernière version mineure de l’ordinateur actuel. Le `C# 7.1` signifie que vous souhaitez utiliser c# 7.1, même après le lancement des nouvelles versions mineures.

![Définition de la version de langue](./media/csharp-7-1/advanced-build-settings.png)

Vous pouvez également modifier le fichier « csproj » et ajouter ou modifier les lignes suivantes :

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Si vous utilisez l’IDE de Visual Studio pour mettre à jour vos fichiers csproj, l’interface IDE crée des nœuds distincts pour chaque configuration de build. Vous devez généralement définir la valeur de la même dans toutes les configurations de build, mais vous devez définir explicitement pour chaque configuration de build, ou sélectionnez « Toutes les Configurations » lorsque vous modifiez ce paramètre. Vous verrez les éléments suivants dans votre fichier csproj :

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Les paramètres appropriés pour le `LangVersion` élément sont :

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

Les chaînes spéciales `default` et `latest` résoudre aux dernières versions majeure et mineure langue installées sur l’ordinateur de build, respectivement.

Ce paramètre dissocie l’installation de nouvelles versions des outils et Kit de développement logiciel dans votre environnement de développement de choisir d’incorporer les nouvelles fonctionnalités de langage dans un projet. Vous pouvez installer les outils et Kit de développement logiciel plus récentes sur votre ordinateur de build. Chaque projet peut être configuré pour utiliser une version spécifique de la langue pour sa génération.

## <a name="async-main"></a>Async principal

Un *async principal* méthode vous permet d’utiliser `await` dans votre `Main` (méthode).
Auparavant, vous deviez écrire :

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Vous pouvez maintenant écrire :

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Si votre programme ne renvoie pas un code de sortie, vous pouvez déclarer un `Main` méthode qui retourne un <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Vous pouvez en savoir plus sur les détails dans le [async principal](../programming-guide/main-and-command-args/index.md) rubrique du guide de programmation.

## <a name="default-literal-expressions"></a>Expressions littérales par défaut

Les expressions littérales par défaut sont une amélioration aux expressions de valeur par défaut.
Ces expressions initialisent une variable à la valeur par défaut. Dans lequel vous précédemment devez écrire :

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Vous pouvez maintenant omettre le type sur le côté droit de l’initialisation :

```csharp
Func<string, bool> whereClause = default;
```

Vous pouvez en savoir plus sur cette fonctionnalité dans la rubrique du Guide de programmation c# sur [par défaut des expressions de valeur](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Cette fonctionnalité modifie également parmi les règles d’analyse pour le [mot clé default](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Noms d’élément de tuple déduit

Cette fonctionnalité est une amélioration de petite à la fonctionnalité de tuples introduite dans c# 7.0. Plusieurs fois lorsque vous initialisez un tuple, les variables utilisées pour le côté droit de l’affectation sont identiques à ceux que vous souhaitez que les éléments de tuple :

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Les noms d’éléments de tuple peuvent être déduits à partir de variables utilisés pour initialiser le tuple dans c# 7.1 :

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Plus d’informations sur cette fonctionnalité dans le [Tuples](../tuples.md) rubrique.

## <a name="reference-assembly-generation"></a>Génération d’assembly de référence

Il existe deux nouvelles options du compilateur qui génèrent des *les assemblys de référence uniquement*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) et [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Les rubriques associées expliquent ces options et les assemblys de référence plus en détail.
