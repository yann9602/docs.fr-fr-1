---
title: "Tuples - Guide C#"
description: "En savoir plus sur les types tuple nommés et sans nom en C#"
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0efb478491ab4c226ec56519c9a957b19ce0478f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="c-tuple-types"></a>Types tuple C# #

Les tuples C# sont des types que vous définissez à l’aide d’une syntaxe simplifiée. Les avantages incluent une syntaxe simplifiée, des règles de conversion basées sur le nombre (appelé « arité ») et les types de champs, et des règles cohérentes pour les copies et les affectations. En échange, les tuples ne prennent pas en charge certains idiomes orientés objet associés à l’héritage. Vous pouvez bénéficier d’une présentation des tuples dans la section correspondante de la rubrique [Nouveautés de C# 7](whats-new/csharp-7.md#tuples).

Dans cette rubrique, vous allez apprendre les règles de langage régissant les tuples dans C# 7, voir différentes façons de les utiliser et bénéficier de conseils de base sur l’utilisation des tuples.

> [!NOTE]
> Les nouvelles fonctionnalités des tuples exigent les types @System.ValueTuple.
> Vous devez ajouter le package NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) pour pouvoir l’utiliser sur les plateformes qui n’incluent pas les types.
>
> Ces fonctionnalités sont semblables à celles d’autres langages qui reposent sur les types fournis dans le framework. `async` et `await` qui reposent sur l’interface `INotifyCompletion`, et LINQ qui repose sur `IEnumerable<T>` en sont des exemples. Toutefois, le mécanisme de remise change à mesure que le .NET dépend de moins en moins de la plateforme. Le .NET Framework n’est pas toujours émis à la même cadence que le compilateur de langage. Quand les nouvelles fonctionnalités de langage reposent sur de nouveaux types, ces types sont disponibles sous la forme de packages NuGet au moment de l’émission des fonctionnalités de langage. À mesure que ces nouveaux types sont ajoutés à l’API .NET Standard et remis dans le cadre du framework, les packages NuGet ne sont plus obligatoires.

Commençons par passer en revue les raisons d’ajouter la nouvelle prise en charge des tuples. Les méthodes retournent un objet unique. Les tuples vous permettent d’empaqueter plus aisément plusieurs valeurs dans cet objet unique. 

Le .NET Framework possède déjà des classes `Tuple` génériques. Ces classes, toutefois, présentaient deux limitations majeures. Premièrement, les classes `Tuple` nommaient leurs champs `Item1`, `Item2`, etc. Ces noms ne comportent aucune information sémantique. L’utilisation de ces types `Tuple` ne permet pas de communiquer la signification de chacun de ces champs. Deuxièmement, les classes `Tuple` sont des types référence. Utiliser un des types `Tuple` signifie allouer des objets. Sur des chemins réactifs, cela peut avoir un impact mesurable sur les performances de votre application.

Pour éviter ces faiblesses, vous pouvez créer une `class` ou un `struct` pour fournir plusieurs champs. Malheureusement, cela génère un surplus de travail et masque votre intention de conception. La création d’un `struct` ou d’une `class` implique la définition d’un type avec des données et un comportement. Souvent, vous souhaitez simplement stocker plusieurs valeurs dans un objet unique.

Les nouvelles fonctionnalités de langage pour les tuples, combinées à un nouvel ensemble de classes dans le Framework, répondent à ces faiblesses. Ces nouveaux tuples utilisent les nouveaux structs `ValueTuple` génériques. Comme son nom l’indique, ce type est un `struct` et non pas une `class`. Il existe différentes versions de ce struct pour prendre en charge des tuples avec différents nombres de champs. La nouvelle prise en charge du langage fournit des noms sémantiques pour les champs de type tuple, ainsi que des fonctionnalités visant à simplifier la construction de champs de tuple ou leur accès.

Les fonctionnalités du langage et les structs génériques `ValueTuple` appliquent la règle stipulant que vous ne pouvez pas ajouter de comportement (méthodes) à ces types tuple.
Tous les types `ValueTuple` sont des *structs mutables*. Chaque champ de membre est un champ public. Cela les rend très légers. Toutefois, cela signifie que les tuples ne doivent pas être utilisés quand l’immuabilité est importante.

Les tuples sont des conteneurs de données plus simples et plus flexibles que les types `class` et `struct`. Examinons ces différences.

## <a name="named-and-unnamed-tuples"></a>Tuples nommés et sans nom

Le struct `ValueTuple` possède des champs nommés `Item1`, `Item2`, `Item3`, etc., similaires aux propriétés définies dans les types `Tuple` existants.
Ces noms sont les seuls noms que vous pouvez utiliser pour les *tuples sans nom*. Quand vous ne fournissez pas de nom de champ alternatif à un tuple, vous avez créé un tuple sans nom :

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Tuple sans nom")]

Toutefois, quand vous initialisez un tuple, vous pouvez utiliser les nouvelles fonctionnalités de langage qui donnent de meilleurs noms aux différents champs. Cette opération crée un *tuple nommé*.
Les tuples nommés ont toujours des champs nommés `Item1`, `Item2`, `Item3`, etc.
Cependant, ils ont également des synonymes pour tous les champs que vous avez nommés.
Vous créez un tuple nommé en spécifiant le nom de chaque champ. Une méthode consiste à spécifier les noms dans le cadre de l’initialisation du tuple :

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Tuple nommé")]

Ces synonymes sont gérés par le compilateur et le langage pour vous permettre d’utiliser efficacement les tuples nommés. Les IDE et les éditeurs peuvent lire ces noms sémantiques à l’aide des API Roslyn. Cela vous permet de référencer les champs d’un tuple nommé par ces noms sémantiques n’importe où dans le même assembly. Le compilateur remplace les noms que vous avez définis par les équivalents `Item*` lors de la génération de la sortie compilée. Le langage MSIL (Microsoft Intermediate Language) compilé n’inclut pas les noms que vous avez donnés à ces champs. 

Le compilateur doit communiquer les noms que vous avez créés pour les tuples qui sont retournés à partir des propriétés et méthodes publiques. Dans ces cas, le compilateur ajoute un attribut `TupleElementNames` sur la méthode. Cet attribut contient une propriété de liste `TransformNames` qui contient les noms attribués à chacun des champs du tuple. 

> [!NOTE]
> Les outils de développement, tels que Visual Studio, lisent également ces métadonnées et fournissent IntelliSense et d’autres fonctionnalités qui utilisent les noms des champs de métadonnées.

Il est important de comprendre les notions de base sous-jacentes des nouveaux tuples et du type `ValueTuple` afin de comprendre les règles d’affectation des tuples nommés entre eux.

## <a name="assignment-and-tuples"></a>Affectation et tuples

Le langage prend en charge l’assignation entre types tuple qui ont le même nombre de champs et les conversions implicites pour les types de chacun de ces champs. Les autres conversions ne sont pas prises en compte pour les affectations. Examinons les types d’affectation qui sont autorisés entre les types tuple.

Prenez en compte les variables utilisées dans les exemples suivants :

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Création de variables")]

Les deux premières variables, `unnamed` et `anonymous`, n’ont pas de noms sémantiques fournis pour les champs. Les noms des champs sont `Item1` et `Item2`.
Les deux dernières variables, `named` et `differentName`, ont des noms sémantiques fournis pour les champs. Notez que ces deux tuples ont des noms différents pour les champs.

Ces quatre tuples ont le même nombre de champs (également appelé « arité ») et les types de ces champs sont identiques. Par conséquent, toutes ces affectations fonctionnent :

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Affectation de variable")]

Notez que les noms des tuples ne sont pas affectés. Les valeurs des champs sont affectées suivant l’ordre des champs dans le tuple.

Des tuples de types différents ou n’ayant pas le même nombre de champs ne sont pas attribuables :

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuples comme valeurs de retour de méthode

L’une des utilisations les plus courantes des tuples est en tant que valeur de retour de méthode. Examinons en détail un exemple. Considérons cette méthode qui calcule l’écart type d’une suite de nombres :

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Calculer l’écart-type")]

> [!NOTE]
> Ces exemples calculent l’écart-type empirique non corrigé.
> La formule de l’écart-type empirique corrigé diviserait la somme des écarts au carré par rapport à la moyenne par (N-1) au lieu de N, comme avec la méthode d’extension `Average`. Pour plus d’informations sur les différences entre ces formules de calcul d’écart-type, consultez un texte de statistiques.

Cette méthode utilise la formule classique de calcul de l’écart-type. Elle génère la réponse correcte, mais constitue une implémentation très peu efficace. Cette méthode énumère deux fois la suite : une fois pour générer la moyenne et une fois pour générer la moyenne quadratique des écarts par rapport à la moyenne.
(Souvenez-vous que les requêtes LINQ sont évaluées de manière différée, de sorte que le calcul des écarts par rapport à la moyenne et de la moyenne de ces écarts effectue une seule énumération.)

Il existe une formule alternative qui calcule l’écart-type à l’aide d’une seule énumération de la suite.  Ce calcul génère deux valeurs en énumérant la suite : la somme de tous les éléments de la suite et la somme de chaque valeur au carré :

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Calculer l’écart-type au moyen de la somme des carrés")]

Cette version énumère une seule fois la séquence. Toutefois, ce code n’est pas facilement réutilisable. En poursuivant votre travail, vous trouverez que de nombreux calculs statistiques différents utilisent le nombre d’éléments dans la suite, la somme de la suite et la somme des carrés de la suite. Refactorisons cette méthode et écrivons une méthode utilitaire qui génère ces trois valeurs.

C’est là que les tuples s’avèrent très utiles. 

Mettons à jour cette méthode afin de stocker dans un tuple les trois valeurs calculées pendant l’énumération. La version suivante est créée :

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactoriser pour utiliser des tuples")]

La prise en charge de la refactorisation par Visual Studio facilite l’extraction des fonctionnalités pour les statistiques principales dans une méthode privée. Cela vous donne une méthode `private static` qui retourne le type tuple avec les trois valeurs de `Sum`, `SumOfSquares` et `Count` :

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "Après extraction de la méthode d’utilitaire")]
 
Le langage met à votre disposition plusieurs autres options, si vous souhaitez apporter quelques modifications rapides à la main. Tout d’abord, vous pouvez utiliser la déclaration `var` pour initialiser le résultat de tuple à partir de l’appel de la méthode `ComputeSumAndSumOfSquares`. Vous pouvez également créer trois variables discrètes à l’intérieur de la méthode `ComputeSumAndSumOfSquares`. La version finale est la suivante :

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "Après le nettoyage final")]

Cette version finale peut être utilisée pour toute méthode qui a besoin de ces trois valeurs ou d’un sous-ensemble quelconque d’entre elles.

Le langage prend en charge d’autres options pour gérer les noms des champs dans ces méthodes retournant des tuples.

Vous pouvez supprimer les noms des champs de la déclaration de la valeur de retour et retourner un tuple sans nom :

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Vous devez traiter les champs de ce tuple comme `Item1`, `Item2` et `Item3`.
Il est recommandé de fournir des noms sémantiques aux champs de tuples retournés par les méthodes.

Un autre idiome pour lequel les tuples peuvent être très utiles est lorsque vous créez des requêtes LINQ et que le résultat final est une projection qui contient certaines propriétés des objets sélectionnés, mais pas toutes.

En règle générale, vous devez projeter les résultats de la requête dans une suite d’objets constituant un type anonyme. Cela présentait de nombreuses limitations, principalement parce que les types anonymes ne pouvaient pas facilement être nommés dans le type de retour pour une méthode. Des coûts importants accompagnaient les alternatives utilisant `object` ou `dynamic` comme type du résultat.

Il est aisé de retourner une séquence d’un type tuple, et les noms et types des champs sont disponibles au moment de la compilation et via les outils de l’IDE.
Considérons, par exemple, une application d’agenda. Vous pouvez définir une classe similaire à la suivante pour représenter une entrée unique dans la liste des tâches :

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "Élément de tâche")]

Vos applications mobiles peuvent prendre en charge une forme compacte des éléments de tâche en cours qui affiche uniquement le titre. Cette requête LINQ effectuerait une projection incluant uniquement l’ID et le titre. Une méthode retournant une suite de tuples exprime très bien cette conception :

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Requête retournant un tuple")]

Le tuple nommé peut faire partie de la signature. Il permet au compilateur et aux outils de l’IDE de vérifier de façon statique que vous utilisez correctement le résultat. Le tuple nommé contient également les informations de type statique, si bien qu’il n’est pas nécessaire d’utiliser des fonctionnalités d’exécution coûteuses telles que la réflexion ou la liaison dynamique pour utiliser les résultats.

## <a name="deconstruction"></a>Déconstruction

Vous pouvez désassembler tous les éléments d’un tuple en *déconstruisant* le tuple retourné par une méthode. Il existe deux approches différentes de la déconstruction des tuples.  Tout d’abord, vous pouvez déclarer explicitement le type de chacun des champs à l’intérieur des parenthèses afin de créer des variables discrètes pour tous les champs du tuple :

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Déconstruire")]

Vous pouvez également déclarer des variables implicitement typées pour chaque champ d’un tuple à l’aide du mot clé `var` en dehors des parenthèses :

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Déconstruire avec var")]

Il est également possible d’utiliser le mot clé `var` avec une ou toutes les déclarations de variables à l’intérieur des parenthèses. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```
Notez que vous ne pouvez pas utiliser un type spécifique en dehors des parenthèses, même si tous les champs du tuple ont le même type.

### <a name="deconstructing-user-defined-types"></a>Déconstruction des types définis par l’utilisateur

N’importe quel type tuple peut être déconstruit comme indiqué ci-dessus. Il est également facile d’activer la déconstruction sur n’importe quel type défini par l’utilisateur (classes, structs ou même interfaces).

L’auteur du type peut définir une ou plusieurs méthodes `Deconstruct` qui affectent des valeurs à un nombre quelconque de variables `out` qui représentent les éléments de données qui composent le type. Par exemple, le type `Person` suivant définit une méthode `Deconstruct` qui déconstruit un objet person en champs représentant le prénom et le nom de famille :

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type avec une méthode deconstruct")]

La méthode deconstruct permet l’attribution à partir d’un objet `Person` de deux chaînes représentant les propriétés `FirstName` et `LastName` :

[!code-csharp[Déconstruire un type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Déconstruire un type de classe")]

Vous pouvez activer la déconstruction même pour des types que vous n’avez pas créés.
La méthode `Deconstruct` peut être une méthode d’extension qui désassemble les membres de données accessibles d’un objet. L’exemple ci-dessous montre un type `Student`, dérivé du type `Person`, et une méthode d’extension qui déconstruit un objet `Student` en trois variables, qui représentent les propriétés `FirstName`, `LastName` et `GPA` :

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type avec une méthode d’extension deconstruct")]

Un objet `Student` a désormais deux méthodes `Deconstruct` accessibles : la méthode d’extension déclarée pour les types `Student` et le membre du type `Person`. Les deux sont dans la portée et cela permet à un objet `Student` d’être déconstruit en deux ou trois variables.
Si vous affectez un étudiant à trois variables, le prénom, le nom de famille et la moyenne pondérée cumulative (GPA) sont tous retournés. Si vous affectez un étudiant à deux variables, seuls le prénom et le nom de famille sont retournés.

[!code-csharp[Méthode d’extension deconstruct](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Déconstruire un type de classe à l’aide d’une méthode d’extension")]

Vous devez être très prudent en définissant plusieurs méthodes `Deconstruct` dans une classe ou une hiérarchie de classes. Plusieurs méthodes `Deconstruct` ayant le même nombre de paramètres `out` peuvent rapidement entraîner des ambiguïtés. Les appelants peuvent ne pas être en mesure d’appeler facilement la méthode `Deconstruct` souhaitée.

Cet exemple présente un risque minimal d’appel ambigu, car la méthode `Deconstruct` pour `Person` a deux paramètres de sortie, et la méthode `Deconstruct` pour `Student` en a trois.

## <a name="conclusion"></a>Conclusion 

La nouvelle prise en charge du langage et de la bibliothèque pour les tuples nommés facilite grandement l’utilisation de conceptions utilisant des structures de données qui stockent plusieurs champs mais ne définissent pas de comportement, telles que les classes et les structs. Il est facile et rapide d’utiliser des tuples pour ces types. Vous obtenez tous les avantages d’une vérification de type statique, sans avoir à créer de types au moyen de la syntaxe `class` ou `struct` plus détaillée. Même ainsi, ils sont particulièrement utiles pour les méthodes utilitaires `private` ou `internal`. Créez des types définis par l’utilisateur, des types `class` ou `struct`, quand vos méthodes publiques retournent une valeur comportant plusieurs champs.

