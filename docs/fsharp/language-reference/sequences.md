---
title: "Séquences (F#)"
description: "Découvrez comment utiliser des séquences de F #, lorsque vous avez une grande collection ordonnée de données mais que vous ne prévoyez pas nécessairement à utiliser tous les éléments."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 23dc7d75-cd26-4df2-9be3-9d1aba5c4443
ms.openlocfilehash: b0562a6efbd2398cd8730bb835a1833955fee1c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="sequences"></a>Séquences

> [!NOTE]
Les liens des informations de référence sur les API qui figurent dans cet article pointent vers MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

A *séquence* est une série logique d’éléments d’un même type. Les séquences sont particulièrement utiles lorsque vous avez une grande collection ordonnée de données mais que vous ne pensez pas nécessairement à utiliser tous les éléments. Séquence des éléments sont calculés uniquement lorsque cela est nécessaire une séquence peut offrir de meilleures performances qu’une liste dans les situations où tous les éléments sont utilisés. Les séquences sont représentées par le `seq<'T>` type, qui est un alias pour `System.Collections.Generic.IEnumerable`. Par conséquent, tout type .NET Framework qui implémente `System.IEnumerable` peut être utilisé comme une séquence. Le [module Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) prend en charge des manipulations qui impliquent des séquences.

## <a name="sequence-expressions"></a>Expressions de séquence
A *expression de séquence* est une expression qui correspond à une séquence. Expressions de séquence peuvent prendre plusieurs formes. La forme la plus simple spécifie une plage. Par exemple, `seq { 1 .. 5 }` crée une séquence qui contienne cinq éléments, y compris les points de terminaison 1 et 5. Vous pouvez également spécifier un incrément (ou décrémenter) entre deux points doubles. Par exemple, le code suivant crée la séquence des multiples de 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Expressions de séquence sont constituées d’expressions F # qui produisent des valeurs de la séquence. Ils peuvent utiliser le `yield` mot clé pour produire des valeurs qui font partie de la séquence.

Voici un exemple.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Vous pouvez utiliser la `->` opérateur à la place de `yield`, auquel cas vous pouvez omettre le `do` (mot clé), comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Le code suivant génère une liste de paires de coordonnées, ainsi que d’un index dans un tableau qui représente la grille.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Un `if` l’expression utilisée dans une séquence est un filtre. Par exemple, pour générer une séquence de nombres premiers uniquement, en supposant que vous avez une fonction `isprime` de type `int -> bool`, construisez la séquence comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Lorsque vous utilisez `yield` ou `->` dans une itération, chaque itération doit générer un élément unique de la séquence. Si chaque itération produit une séquence d’éléments, utilisez `yield!`. Dans ce cas, les éléments générés sur chaque itération sont concaténés pour produire la séquence finale.

Vous pouvez combiner plusieurs expressions dans une expression de séquence. Les éléments générés par chaque expression sont concaténés. Pour obtenir un exemple, consultez la section « Exemples » de cette rubrique.

## <a name="examples"></a>Exemples
Le premier exemple utilise une expression de séquence qui contient une itération, un filtre et une instruction yield pour générer un tableau. Ce code imprime une séquence de nombres premiers entre 1 et 100 dans la console.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Le code suivant utilise `yield` pour créer une table de multiplication qui se compose de tuples de trois éléments, chacun d'entre eux comprenant deux facteurs et le produit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

L’exemple suivant illustre l’utilisation de `yield!` pour combiner des séquences individuelles en une séquence finale unique. Dans ce cas, les séquences de chaque sous-arborescence dans une arborescence binaire sont concaténées dans une fonction récursive pour produire la séquence finale.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a>À l’aide de séquences
Séquences prennent en charge la plupart des fonctions identiques à celles [répertorie](lists.md). Les séquences prennent également en charge des opérations telles que le regroupement et le décompte à l’aide de fonctions de génération de clé. Les séquences prennent également en charge les fonctions plus diverses pour l’extraction de sous-séquences.

Nombreux types de données, telles que les listes, les tableaux, les jeux et les mappages sont implicitement des séquences, car ils sont des collections énumérables. Une fonction qui accepte une séquence comme un argument fonctionne avec les types de données F # courants, en outre à n’importe quel type de données .NET Framework qui implémente `System.Collections.Generic.IEnumerable<'T>`. Comparez cela à une fonction qui accepte une liste en tant qu’argument, ce qui peut prendre uniquement les listes. Le type `seq<'T>` est une abréviation de type pour `IEnumerable<'T>`. Cela signifie que n’importe quel type qui implémente l’objet générique `System.Collections.Generic.IEnumerable<'T>`, qui inclut des tableaux, listes, définit et mappages en F # et également la plupart des .NET Framework types de collection, est compatible avec le `seq` de type et peut être utilisé partout où une séquence est attendue.


## <a name="module-functions"></a>Fonctions de module
Le [module Seq](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) dans les [espace de noms Microsoft.FSharp.Collections](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contient des fonctions pour l’utilisation des séquences. Ces fonctions utilisent des listes, les tableaux, les mappages et les jeux, étant donné que tous ces types sont énumérables et par conséquent, peuvent être traitées comme des séquences.


## <a name="creating-sequences"></a>Création de séquences
Vous pouvez créer des séquences à l’aide d’expressions de séquence, comme décrit précédemment, ou en utilisant certaines fonctions.

Vous pouvez créer une séquence vide à l’aide de [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), ou vous pouvez créer une séquence d’un seul élément spécifié à l’aide de [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Vous pouvez utiliser [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) pour créer une séquence pour laquelle les éléments sont créés à l’aide d’une fonction que vous fournissez. Vous fournissez également une taille pour la séquence. Cette fonction est comparable à [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), sauf que les éléments ne sont pas créés jusqu'à ce que vous itérez au sein de la séquence. Le code suivant illustre l’utilisation de `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

La sortie est la suivante :

```
0 10 20 30 40
```

À l’aide de [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) et [Seq.ofList &#60;' T &#62; Fonction](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), vous pouvez créer des séquences de tableaux et listes. Toutefois, vous pouvez également convertir tableaux et listes aux séquences à l’aide d’un opérateur de conversion. Ces deux techniques sont affichés dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

À l’aide de [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), vous pouvez créer une séquence à partir d’une collection faiblement typée, tels que ceux définis dans `System.Collections`. Ces collections faiblement typées ont le type d’élément `System.Object` sont énumérées à l’aide de la non générique `System.Collections.Generic.IEnumerable&#96;1` type. Le code suivant illustre l’utilisation de `Seq.cast` pour convertir un `System.Collections.ArrayList` en une séquence.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Vous pouvez définir des séquences infinies à l’aide de la [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) (fonction). Pour une séquence de ce type, vous fournissez une fonction qui génère chaque élément à partir de l’index de l’élément. Les séquences infinies sont possibles en raison de l’évaluation différée ; éléments sont créés en fonction des besoins en appelant la fonction que vous spécifiez. L’exemple de code suivant produit une séquence infinie de nombres à virgule flottante, dans ce cas, la série en alternance des réciproques des carrés des entiers consécutifs.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) génère une séquence à partir d’une fonction de calcul qui prend un état et le transforme pour produire chaque élément suivant dans la séquence. L’état est simplement une valeur qui est utilisée pour calculer chaque élément et peut changer que chaque élément est calculé. Le deuxième argument de `Seq.unfold` est la valeur initiale est utilisée pour démarrer la séquence. `Seq.unfold`utilise un type d’option pour l’état, ce qui vous permet de terminer la séquence en retournant la `None` valeur. Le code suivant montre deux exemples de séquences, `seq1` et `fib`, qui sont générés par une `unfold` opération. La première, `seq1`, est juste une séquence simple avec des nombres jusqu'à 100. La seconde, `fib`, utilise `unfold` pour calculer la séquence de Fibonacci. Étant donné que chaque élément de la séquence de Fibonacci est la somme de deux nombres de Fibonacci précédents, la valeur d’état est un tuple qui se compose de deux nombres précédents de la séquence. La valeur initiale est `(1,1)`, les deux premiers nombres dans la séquence.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

La sortie est la suivante :

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Le code suivant est un exemple qui utilise de nombreuses fonctions de module de séquence décrites ici pour générer et calculer les valeurs de séquences infinies. Le code peut prendre quelques minutes pour s’exécuter.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a>Recherche d’éléments
Séquences prennent en charge les fonctionnalités disponibles avec les listes : [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), et [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Les versions de ces fonctions sont disponibles pour les séquences évaluent la séquence uniquement jusqu'à l’élément qui est en cours de recherche. Pour obtenir des exemples, consultez [répertorie](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).


## <a name="obtaining-subsequences"></a>Obtention de sous-séquences
[Seq.Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) et [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) sont comme les fonctions correspondantes qui sont disponibles pour les listes, sauf que le filtrage et le choix ne se produit pas jusqu'à ce que les éléments de la séquence sont évaluées.

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) crée une séquence à partir d’une autre séquence, mais limite la séquence à un nombre spécifié d’éléments. [Seq.Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) crée une séquence qui contient uniquement un nombre spécifié d’éléments à partir du début d’une séquence. S’il existe moins d’éléments dans la séquence que vous spécifiez pour tirer, `Seq.take` lève une `System.InvalidOperationException`. La différence entre `Seq.take` et `Seq.truncate` qui est `Seq.truncate` ne produit pas une erreur si le nombre d’éléments est inférieur au nombre que vous spécifiez.

Le code suivant montre le comportement d’et les différences entre `Seq.truncate` et `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

La sortie, avant que l’erreur se produit, est la suivante.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

À l’aide de [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), vous pouvez spécifier une fonction de prédicat (fonction booléenne) et créer une séquence à partir d’une autre séquence composée des éléments de la séquence d’origine pour lequel le prédicat est `true`, mais arrêter avant le premier élément pour lequel le prédicat retourne `false`. [Seq.Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) retourne une séquence qui ignore un nombre spécifié des premiers éléments d’une autre séquence et retourne les éléments restants. [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) retourne une séquence qui ignore les premiers éléments d’une autre séquence tant que le prédicat retourne `true`, puis retourne les éléments restants, en commençant par le premier élément pour lequel le prédicat retourne `false`.

L’exemple de code suivant illustre le comportement d’et les différences entre `Seq.takeWhile`, `Seq.skip`, et `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

La sortie est la suivante.

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformation de séquences
[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) crée une séquence dans laquelle les éléments consécutifs de la séquence d’entrée sont regroupés dans des tuples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.Windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) est similaire à `Seq.pairwise`, mais au lieu de produire une séquence de tuples, elle produit une séquence de tableaux qui contiennent des copies d’éléments adjacents (un *fenêtre*) à partir de la séquence. Vous spécifiez le nombre d’éléments adjacents que vous souhaitez dans chaque tableau.

L'exemple de code suivant montre l'utilisation de `Seq.windowed`. Dans ce cas, le nombre d’éléments dans la fenêtre est 3. L’exemple utilise `printSeq`, qui est défini dans l’exemple de code précédent.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

La sortie est la suivante.

Séquence d’origine :

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Opérations avec plusieurs séquences
[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) et [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) prennent deux ou trois séquences et produisent une séquence de tuples. Ces fonctions sont comme les fonctions correspondantes disponibles pour [répertorie](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Il n’existe aucune fonctionnalité correspondante pour séparer une séquence en deux ou plusieurs séquences. Si vous avez besoin de cette fonctionnalité pour une séquence, convertissez-la en une liste et utilisez [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).


## <a name="sorting-comparing-and-grouping"></a>Tri, de comparaison et de regroupement
Les fonctions de tri prises en charge pour les listes fonctionnent également avec les séquences. Cela inclut les [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) et [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Ces fonctions itèrent l’intégralité de la séquence.

Vous comparez deux séquences à l’aide de la [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) (fonction). La fonction compare les éléments consécutifs à son tour et s’arrête lorsqu’il rencontre la première paire inégale. Tous les éléments supplémentaires ne contribuent pas à la comparaison.

Le code suivant illustre l'utilisation de `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

Dans le code précédent, seul le premier élément est calculé et examiné, et le résultat est -1.

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) prend une fonction qui génère une valeur appelée un *clé* pour chaque élément. Une clé est générée pour chaque élément en appelant cette fonction sur chaque élément. `Seq.countBy`retourne ensuite une séquence qui contient les valeurs de clé et le nombre d’éléments ayant généré chaque valeur de la clé.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

La sortie est la suivante.

```
(1, 34) (2, 33) (0, 33)
```

La sortie précédente indique qu’il existait 34 d’éléments de la séquence d’origine qui a généré la clé 1, 33 valeurs qui produit la clé 2 et 33 qui produit la clé 0.

Vous pouvez regrouper les éléments d’une séquence en appelant [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy`prend une séquence et une fonction qui génère une clé à partir d’un élément. La fonction est exécutée sur chaque élément de la séquence. `Seq.groupBy`Retourne une séquence de tuples, où le premier élément de chaque tuple est la clé et le second est une séquence d’éléments qui produisent la clé.

L’exemple de code suivant illustre l’utilisation de `Seq.groupBy` pour partitionner la séquence de nombres de 1 à 100 en trois groupes qui ont les valeurs de clés distinctes, 0, 1 et 2.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

La sortie est la suivante.

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Vous pouvez créer une séquence qui élimine des éléments en double en appelant [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Vous pouvez également utiliser [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), qui prend une fonction génératrice de clé à appeler sur chaque élément. La séquence résultante contient les éléments de la séquence d’origine qui ont des clés uniques ; éléments ultérieurs qui produisent une clé en double d’un élément antérieur sont ignorés.

L’exemple de code suivant illustre l’utilisation de `Seq.distinct`. `Seq.distinct`est illustrée en générant des séquences qui représentent des nombres binaires, puis en montrant que les seuls éléments distincts sont 0 et 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Le code suivant montre comment `Seq.distinctBy` en commençant par une séquence qui contient les nombres positifs et négatifs, à l’aide de la fonction de valeur absolue comme fonction génératrice de clé. La séquence résultante est manquant pour tous les nombres positifs qui correspondent aux nombres négatifs de la séquence, étant donné que les nombres négatifs apparaissent plus tôt dans la séquence et par conséquent sont sélectionnées au lieu des nombres positifs qui ont le même absolue valeur, ou la clé.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a>En lecture seule et les séquences de mise en cache
[Seq.ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) crée une copie en lecture seule d’une séquence. `Seq.readonly`est utile lorsque vous avez une collection en lecture-écriture, tel qu’un tableau, et vous ne souhaitez pas modifier la collection d’origine. Cette fonction peut être utilisée pour conserver l’encapsulation de données. Dans l’exemple de code suivant, un type qui contient un tableau est créé. Une propriété expose le tableau, mais au lieu de retourner un tableau, elle retourne une séquence qui est créée à partir du tableau à l’aide de `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) crée une version stockée d’une séquence. Utilisez `Seq.cache` pour éviter la réévaluation d’une séquence, ou lorsque vous avez plusieurs threads qui utilisent une séquence, mais vous devez vous assurer que chaque élément est traité qu’une seule fois. Lorsque vous avez une séquence qui est utilisée par plusieurs threads, vous pouvez avoir un thread qui énumère et calcule les valeurs de la séquence d’origine, et les autres threads qui utilisent la séquence de mise en cache.


## <a name="performing-computations-on-sequences"></a>Effectuer des calculs sur les séquences
Opérations arithmétiques simples sont comme celles des listes, tel que [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), et ainsi de suite.

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), et [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) sont comme les fonctions correspondantes qui sont disponibles pour les listes. Séquences prennent en charge un sous-ensemble des variations complètes de ces fonctions qui répertorie la prise en charge. Pour plus d’informations et d’exemples, consultez [répertorie](lists.md).

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Types F#](fsharp-types.md)
