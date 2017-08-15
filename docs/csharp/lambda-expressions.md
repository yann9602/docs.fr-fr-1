---
title: Expressions lambda
description: "Découvrez comment utiliser des expressions lambda, qui sont des blocs de code exécutable qui peuvent être passés comme arguments."
keywords: ".NET, .NET Core, expressions lambda, lambdas, délégués"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.translationtype: HT
ms.sourcegitcommit: 2762cdc983465979a530192716c33de7044dd1ed
ms.openlocfilehash: 659a3366b00d6abe6598c31774d008c6b8f400fd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/04/2017

---

# <a name="lambda-expressions"></a>Expressions lambda #

Une *expression lambda* est un bloc de code (une expression ou un bloc d’instructions) qui est traité comme un objet. Elle peut être passée comme argument à des méthodes, et peut aussi être retournée par des appels de méthode. Les expressions lambda sont largement utilisées pour :

- Passer le code à exécuter à des méthodes asynchrones, comme @System.Threading.Tasks.Task.Run(System.Action).

- Écrire des [expressions de requête LINQ](linq/index.md).

- Créer des [arborescences d’expressions](expression-trees-building.md).

Les expressions lambda sont du code qui peut être représenté comme un délégué, ou comme une arborescence d’expressions qui est compilée en délégué. Le type délégué spécifique d’une expression lambda dépend de ses paramètres et de sa valeur de retour. Les expressions lambda qui ne retournent pas de valeur correspondent à un délégué `Action` spécifique, en fonction du nombre de ses paramètres. Les expressions lambda qui retournent une valeur correspondent à un délégué `Func` spécifique, en fonction du nombre de ses paramètres. Par exemple, une expression lambda qui a deux paramètres mais qui ne retourne aucune valeur correspond à un délégué @System.Action%602. Une expression lambda qui a un paramètre et qui retourne une valeur correspond à un délégué @System.Func%602.

Une expression lambda utilise `=>`, l’[opérateur de déclaration lambda](language-reference/operators/lambda-operator.md), pour séparer la liste des paramètres de l’expression lambda de son code exécutable. Pour créer une expression lambda, vous spécifiez des paramètres d’entrée (le cas échéant) du côté gauche de l’opérateur lambda, et vous placez l’expression ou le bloc d’instructions de l’autre côté. Par exemple, l’expression lambda d’une seule ligne `x => x * x` spécifie un paramètre nommé `x` et retourne la valeur `x` élevée au carré. Vous pouvez assigner cette expression à un type délégué, comme dans l'exemple suivant :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Vous pouvez aussi le passer directement comme argument de méthode :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Expressions lambdas ##

 Une expression lambda avec une expression du côté droit de l’opérateur => est appelée *expression lambda*. Les expressions lambda sont utilisées en grand nombre dans la construction d’[arborescences d’expressions](expression-trees.md). Une expression lambda retourne le résultat de l'expression et prend la forme de base suivante :

```csharp
(input parameters) => expression
```

Les parenthèses sont facultatives uniquement si le lambda comporte un paramètre d'entrée ; sinon, elles sont obligatoires. Utilisez des parenthèses vides s'il n'y a aucun paramètre d'entrée :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Les paramètres d'entrée sont séparés par des virgules entre parenthèses :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

En règle générale, le compilateur utilise l’inférence de type pour déterminer les types des paramètres. Il est cependant parfois difficile, voire impossible, pour le compilateur d’inférer les types en entrée. Dans ce cas, vous pouvez spécifier les types explicitement, comme dans l’exemple suivant :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Notez dans l'exemple précédent que le corps d'une expression lambda peut se composer d'un appel de méthode. Toutefois, si vous créez des arborescences d’expressions qui sont évaluées en dehors du .NET Framework, comme dans SQL Server ou Entity Framework (EF), vous devez éviter d’utiliser les appels de méthode dans les expressions lambda, car les méthodes peuvent n’avoir aucune signification en dehors du contexte de l’implémentation .NET. Si vous choisissez d’utiliser des appels de méthode dans ce cas, veillez à les tester minutieusement pour vérifier que ces appels de méthode peuvent être résolus correctement.

## <a name="statement-lambdas"></a>Instructions lambda ##

Une instruction lambda ressemble à une expression lambda, mais l'instruction ou les instructions sont mises entre accolades :

```csharp
(input parameters) => { statement; }
```

Le corps d'une instruction lambda peut se composer d'un nombre illimité d'instructions ; toutefois, en pratique, leur nombre est généralement de deux ou trois.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Les instructions lambda, comme les méthodes anonymes, ne peuvent pas être utilisées pour créer des arborescences d'expression.

## <a name="async-lambdas"></a>Lambdas asynchrones ##

Vous pouvez facilement créer des expressions et des instructions lambda qui incorporent un traitement asynchrone en utilisant les mots clés [async](language-reference/keywords/async.md) et [await](language-reference/keywords/await.md). Ainsi, l’exemple appelle une méthode `ShowSquares` qui s’exécute de façon asynchrone.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Pour plus d’informations sur la création et l’utilisation des méthodes asyncrones, consultez [Programmation asynchrone avec async et await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Expressions lambda et tuples ##

À compter sa version 7.0, le langage C# offre la prise en charge intégrée des tuples. Vous pouvez fournir un tuple comme argument à une expression lambda, et votre expression lambda peut aussi retourner un tuple. Dans certains cas, le compilateur C# utilise l’inférence de type pour déterminer les types des composants du tuple. 

Vous définissez un tuple en plaçant entre des parenthèses une liste de ses composants avec des virgules comme séparateur. L’exemple suivant utilise un tuple avec 5 composants pour passer une séquence de nombres à une expression lambda, qui double chaque valeur et retourne un tuple avec 5 composants qui contient le résultat des multiplications.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

En général, les champs d’un tuple sont nommés `Item1`, `Item2`, etc. Vous pouvez cependant définir un tuple avec des composants nommés, comme dans l’exemple suivant.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Pour plus d’informations sur la prise en charge des tuples en C#, consultez [Types tuple de C#](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas avec les opérateurs de requête standard ##

LINQ to Objects, parmi d’autres implémentations, a un paramètre d’entrée dont le type fait partie de la famille @System.Func%601 de délégués génériques. Ces délégués utilisent des paramètres de type pour définir le nombre et le type des paramètres d’entrée, ainsi que le type de retour du délégué. Les délégués `Func` sont très utiles pour l'encapsulation des expressions définies par l'utilisateur appliquées à chaque élément dans un jeu de données sources. Par exemple, considérez le délégué @System.Func%601, dont la syntaxe est :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Le délégué peut être instancié avec du code similaire à celui-ci,

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

où `int` est un paramètre d’entrée et `bool` est la valeur de retour. La valeur de retour est toujours spécifiée dans le dernier paramètre de type. Quand le délégué `Func` suivant est appelé, il retourne la valeur true ou false pour indiquer si le paramètre d’entrée est égal à 5 :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Vous pouvez aussi fournir une expression lambda quand le type d’argument est @System.Linq.Expressions.Expression%601, par exemple dans les opérateurs de requête standard définis dans le type @System.Linq.Queryable. Quand vous spécifiez un argument @System.Linq.Expressions.Expression%601, le lambda est compilé en une arborescence d’expressions. L’exemple suivant utilise l’opérateur de requête standard [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})).

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Le compilateur peut déduire le type du paramètre d'entrée, ou vous pouvez également le spécifier explicitement. Cette expression lambda particulière compte ces entiers (`n`) qui, quand ils sont divisés par deux, ont un reste égal à 1.

L’exemple suivant produit une séquence qui contient tous les éléments du tableau `numbers` qui précèdent le 9, car c’est le premier nombre de la séquence qui ne satisfait pas la condition.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

L’exemple suivant spécifie plusieurs paramètres d’entrée en les plaçant entre parenthèses. La méthode retourne tous les éléments du tableau de nombres jusqu’à ce qu’elle rencontre un nombre dont la valeur est inférieure à sa position ordinale dans le tableau.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Inférence de type et expressions lambda ##

Quand vous écrivez des lambdas, vous n’avez généralement pas à spécifier un type pour les paramètres d’entrée, car le compilateur peut inférer le type en fonction du corps du lambda, des types de paramètre et d’autres facteurs, comme décrit dans la spécification du langage C#. Pour la plupart des opérateurs de requête standard, la première entrée est le type des éléments dans la séquence source. Si vous interrogez un `IEnumerable<Customer>`, le type de la variable d’entrée est inféré comme étant un objet `Customer`, ce qui signifie que vous avez accès à ses méthodes et à ses propriétés :

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Les règles générales de l’inférence de type pour les lambdas sont :

- Le lambda doit contenir le même nombre de paramètres que le type délégué.

- Chaque argument d’entrée dans le lambda doit être implicitement convertible en son paramètre de délégué correspondant.

- La valeur de retour du lambda (le cas échéant) doit être implicitement convertible en type de retour du délégué.

Notez que les expressions lambda en elles-mêmes n'ont pas de type, car le système de type commun (CTS, Common Type System) ne comporte aucun concept intrinsèque « d'expression lambda ». Toutefois, il est parfois commode de parler de manière informelle du « type » d'une expression lambda. Dans ce cas, le type fait référence au type délégué ou au type @System.Linq.Expressions.Expression dans lequel est convertie l'expression lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Portée variable dans les expressions lambda ##

Les lambdas peuvent faire référence à des *variables externes* (consultez [Méthodes anonymes](programming-guide/statements-expressions-operators/anonymous-methods.md)) qui se trouvent dans l’étendue de la méthode qui définit la fonction lambda, ou dans l’étendue du type qui contient l’expression lambda. Les variables capturées de cette manière sont stockées pour une utilisation dans l'expression lambda, même si les variables se trouvent en dehors de la portée et sont récupérées par le garbage collector. Une variable externe doit être assignée de manière précise pour pouvoir être utilisée dans une expression lambda. L’exemple suivant illustre ces règles.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Les règles suivantes s'appliquent à la portée des variables dans les expressions lambda :

- Une variable qui est capturée ne sera pas récupérée par le garbage collector avant que le délégué qui le référence soit disponible pour le garbage collection.

- Les variables introduites dans une expression lambda ne sont pas visibles dans la méthode externe.

- Une expression lambda ne peut pas capturer directement un paramètre `ref` ou `out` dans une méthode englobante.

- Une instruction return dans une expression lambda ne provoque pas le retour de la méthode englobante.

- Une expression lambda ne peut pas contenir une instruction `goto` , une instruction `break` , ou une instruction `continue` à l'intérieur de la fonction lambda si la cible de l'instruction de saut est hors du bloc. C'est également une erreur d'avoir une instruction de saut en dehors du bloc de la fonction lambda si la cible est à l'intérieur du bloc.

## <a name="see-also"></a>Voir aussi ##

[LINQ (Language-Integrated Query)](../standard/using-linq.md)   
[Méthodes anonymes](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[Arborescences d’expressions](expression-trees.md)

