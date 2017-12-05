---
title: "Sémantique de référence avec les types valeur"
description: "Comprendre les fonctionnalités de langage conçues pour minimiser les structures de copie en toute sécurité"
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 0c6e44a3e1a1458f4211b66b6d1ef5b4b30cd7c1
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="reference-semantics-with-value-types"></a>Sémantique de référence avec les types valeur

L’avantage des types valeur est qu’ils permettent souvent d’éviter les allocations de tas.
Mais l’inconvénient, c’est qu’ils sont copiés par valeur. Ce compromis complique l’optimisation des algorithmes qui opèrent sur de grandes quantités de données. Les nouvelles fonctionnalités de langage dans C# 7.2 fournissent des mécanismes qui permettent la sémantique de passage par référence avec des types valeur. Si vous utilisez ces fonctionnalités judicieusement, vous pouvez minimiser à la fois les allocations et les opérations de copie. Cet article explore ces nouvelles fonctionnalités.

Une grande partie de l’exemple de code de cet article illustre les fonctionnalités ajoutées dans C# 7.2. Pour pouvoir utiliser ces fonctionnalités, vous devez configurer votre projet de telle sorte qu’il utilise C# 7.2 ou ultérieur. Vous pouvez utiliser Visual Studio pour le sélectionner. Pour chaque projet, sélectionnez **Projet** dans le menu, puis **Propriétés**. Sélectionnez l’onglet **Build**, puis cliquez sur **Avancé**. À partir de là, vous pouvez configurer la version du langage. Choisissez « 7.2 », ou « dernière ».  Sinon, vous pouvez modifier le fichier *csproj* et ajouter le nœud suivant :

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Vous pouvez utiliser « 7.2 » ou « dernière » comme valeur.

## <a name="specifying-in-parameters"></a>Spécification des paramètres `in`

C# 7.2 ajoute le mot clé `in` pour compléter les mots clés `ref` et `out` existants quand vous écrivez une méthode qui passe des arguments par référence. Le mot clé `in` spécifie que vous passez le paramètre par référence et que la méthode appelée ne modifie pas la valeur qui lui est passée. 

Vous disposez ainsi d’un vocabulaire complet pour exprimer votre intention de conception. Les types valeur sont copiés s’ils sont passés à une méthode appelée et que vous ne spécifiez pas l’un des modificateurs suivants. Chacun de ces modificateurs spécifie qu’un type valeur est passé par référence, évitant ainsi la copie. Chaque modificateur exprime une intention différente :

- `out` : Cette méthode définit la valeur de l’argument utilisé comme paramètre.
- `ref` : Cette méthode peut définir la valeur de l’argument utilisé comme paramètre.
- `in` : Cette méthode ne modifie pas la valeur de l’argument utilisé comme paramètre.

Quand vous ajoutez le modificateur `in` pour passer un argument par référence, vous déclarez que votre intention de conception est de passer des arguments par référence afin d’éviter toute copie inutile. Vous n’avez pas l’intention de modifier l’objet utilisé comme argument. Le code suivant montre un exemple de méthode qui calcule la distance entre deux points dans l’espace 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Les arguments sont deux structures qui contiennent chacune trois valeurs de type double. Un double représentant 8 octets, chaque argument représente 24 octets. En spécifiant le modificateur `in`, vous passez une référence de 4 ou 8 octets à ces arguments, selon l’architecture de l’ordinateur. La différence de taille est minime, mais elle peut rapidement s’accentuer si votre application appelle cette méthode dans une boucle serrée avec de nombreuses valeurs différentes.
 
Le modificateur `in` complète aussi `out` et `ref` d’autres façons. Vous ne pouvez pas créer de surcharges d’une méthode qui diffèrent uniquement en présence de `in`, `out` ou `ref`. Ces nouvelles règles étendent le même comportement qui a toujours été défini pour les paramètres `out` et `ref`.

Le modificateur `in` peut être appliqué à tout membre acceptant des paramètres : méthodes, délégués, expressions lambda, fonctions locales, indexeurs, opérateurs.

Contrairement aux arguments `ref` et `out`, vous pouvez utiliser des constantes ou des valeurs littérales pour l’argument à un paramètre `in`. Par ailleurs, contrairement à un paramètre `ref` ou `out`, il est inutile d’appliquer le modificateur `in` au niveau du site d’appel. Le code suivant donne deux exemples d’appel de la méthode `CalculateDistance`. Le premier utilise deux variables locales passées par référence. La deuxième inclut une variable temporaire créée dans le cadre de l’appel de méthode. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Le compilateur veille de plusieurs manières à l’application du principe « en lecture seule » d’un argument `in`.  Premièrement, la méthode appelée ne peut rien assigner directement à un paramètre `in`. Elle ne peut rien assigner directement aux champs d’un paramètre `in`. Par ailleurs, vous ne pouvez pas passer un paramètre `in` à une méthode exigeant le modificateur `ref` ou `out`.
Le compilateur veille à ce que l’argument `in` soit une variable en lecture seule. Vous pouvez appeler n’importe quelle méthode d’instance qui utilise une sémantique de passage par valeur. Dans ces instances, une copie du paramètre `in` est créée. Étant donné que le compilateur peut créer une variable temporaire pour tout paramètre `in`, vous pouvez également spécifier des valeurs par défaut pour tout paramètre `in`. Pour illustrer ceci, le code suivant spécifie l’origine (point 0,0) comme valeur par défaut pour le deuxième point :

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

La désignation du paramètre `in` peut également être utilisée avec des types référence ou générée dans les valeurs numériques. Toutefois, les avantages dans les deux cas sont minimes, voire inexistants.

## <a name="ref-readonly-returns"></a>Retours `ref readonly`

Vous pouvez également retourner un type valeur par référence, mais interdire à l’appelant de modifier cette valeur. Pour exprimer cette intention de conception, utilisez le modificateur `ref readonly`. Celui-ci indique aux lecteurs que vous retournez une référence à des données existantes, mais que vous n’autorisez aucune modification. 

Le compilateur fait en sorte que l’appelant ne puisse pas modifier la référence. Toute tentative d’assignation directe à la valeur génère une erreur de compilation. Toutefois, le compilateur ne peut pas savoir si une méthode membre modifie l’état du struct.
Pour vérifier que l’objet n’est pas modifié, le compilateur crée une copie et appelle les références de membre à l’aide de cette copie. Les modifications sont apportées à cette copie défensive. 

Il est probable que la bibliothèque utilisant `Point3D` ait recours à l’origine dans tout le code. Chaque instance crée un objet sur la pile. Il peut être avantageux de créer une constante et de la retourner par référence. Mais si vous retournez une référence à un stockage interne, il peut être judicieux de veiller à ce que l’appelant ne puisse pas modifier le stockage référencé. Le code suivant définit une propriété en lecture seule qui retourne un `readonly ref` à un `Point3D` qui spécifie l’origine.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Pour créer une copie d’un ref readonly return, il vous suffit de l’assigner à une variable non déclarée avec le modificateur `ref readonly`. Le compilateur génère du code pour copier l’objet dans le cadre de l’assignation. 

Quand vous assignez une variable à un `ref readonly return`, vous pouvez spécifier une variable `ref readonly` ou une copie par valeur de la référence en lecture seule :

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

La première assignation dans le code précédent effectue une copie de la constante `Origin` et assigne cette copie. La seconde assigne une référence. Notez que le modificateur `readonly` doit faire partie de la déclaration de la variable. La référence à laquelle il fait référence ne peut pas être modifiée. Toute tentative de modification provoque une erreur de compilation.

## <a name="readonly-struct-type"></a>Type `readonly struct`

L’application de `ref readonly` à des utilisations à trafic élevé d’un struct peut suffire.
Dans d’autres cas, il peut-être préférable de créer un struct immuable. Vous pouvez toujours passer des valeurs par référence en lecture seule. Cette pratique supprime les copies défensives qui se produisent quand vous accédez aux méthodes d’un struct utilisé comme paramètre `in`.

Pour cela, créez un type `readonly struct`. Ajoutez le modificateur `readonly` à une déclaration de struct. Le compilateur veille à ce que tous les membres d’instance du struct soient `readonly` ; le `struct` doit être immuable.

Il existe d’autres optimisations pour un `readonly struct`. Vous pouvez utiliser le modificateur `in` à chaque emplacement où `readonly struct` est un argument. En outre, vous pouvez retourner un `readonly struct` comme `ref return` quand vous retournez un objet dont la durée de vie s’étend au-delà de la portée de la méthode retournant l’objet.

Enfin, le compilateur génère du code plus performant quand vous appelez les membres d’un `readonly struct` : la référence `this`, et non une copie du récepteur, est toujours un paramètre `in` passé par référence à la méthode de membre. Cette optimisation évite d’autres opérations de copie quand vous utilisez un `readonly struct`. `Point3D` est un bon candidat pour ce changement. Le code suivant illustre une structure `ReadonlyPoint3D` mise à jour :

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>Type `ref struct`

Une autre fonctionnalité de langage associé est la possibilité de déclarer un type valeur qui doit être alloué par la pile. En d’autres termes, ces types ne peuvent jamais être créés sur le tas comme membres d’une autre classe. Cette fonctionnalité vise principalement <xref:System.Span%601> et ses structures associées. <xref:System.Span%601> peut contenir un pointeur managé comme l’un de ses membres, l’autre étant la longueur de l’étendue. En fait, il est implémenté un peu différemment, car C# ne prend pas en charge les pointeurs vers la mémoire managée en dehors d’un contexte unsafe. Toute écriture qui change le pointeur et la longueur n’est pas atomique. Cela signifie qu’un <xref:System.Span%601> ferait l’objet d’erreurs « hors limites » ou d’autres violations de cohérence des types s’il n’était pas limité à un frame de pile. De plus, le fait de placer un pointeur managé sur le tas GC entraîne généralement un blocage au moment de JIT.

Vous pouvez avoir des exigences similaires quand vous utilisez de la mémoire créée avec [`stackalloc`](language-reference/keywords/stackalloc.md) ou de la mémoire provenant d’API d’interopérabilité. Pour répondre à ces besoins, vous pouvez définir vos propres types `ref struct`. Par souci de simplicité, cet article comprend des exemples d’utilisation de `Span<T>`.

La déclaration `ref struct` déclare qu’un struct de ce type doit être sur la pile. Les règles de langage garantissent l’utilisation sécurisée de ces types. Parmi les autres types déclarés comme `ref struct`, citons <xref:System.ReadOnlySpan%601>. 

La conservation d’un type `ref struct` comme variable allouée par la pile introduit plusieurs règles que le compilateur applique pour tous les types `ref struct`.

- Vous ne pouvez pas effectuer d’opération box sur un `ref struct`. Vous ne pouvez pas assigner un type `ref struct` à une variable de type `object`, `dynamic` ou tout type interface.
- Vous ne pouvez pas déclarer `ref struct` comme membre d’une classe ou d’un struct normal.
- Vous ne pouvez pas déclarer des variables locales qui sont des types `ref struct` dans des méthodes async. Vous pouvez les déclarer dans des méthodes synchrones qui retournent `Task`, `Task<T>` ou des types similaires à Task.
- Vous ne pouvez pas déclarer de variables locales `ref struct` dans des itérateurs.
- Vous ne pouvez pas capturer de variables `ref struct` dans des expressions lambda ou des fonctions locales.

Ces restrictions vous empêchent d’utiliser accidentellement un `ref struct` d’une manière qui pourrait le promouvoir au niveau du tas managé.

## <a name="conclusions"></a>Conclusions

Ces améliorations apportées au langage C# sont conçues pour les algorithmes axés sur les performances dans lesquels les allocations de mémoire peuvent être essentielles pour atteindre le niveau de performance nécessaire. Vous constaterez peut-être que vous n’utilisez pas souvent ces fonctionnalités dans votre code. Toutefois, ces améliorations ont été adoptées à divers endroits du .NET Framework. Au fur et à mesure que les API adoptent ces fonctionnalités, vous verrez les performances de vos propres applications s’améliorer.
