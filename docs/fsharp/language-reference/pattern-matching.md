---
title: "Critères spéciaux (F#)"
description: "Découvrez comment les modèles sont utilisés en F # pour comparer des données avec les structures logiques, décomposer les données en parties constituantes ou extraire des informations à partir des données."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a>Critères spéciaux

Les modèles sont des règles de transformation des données d’entrée. Elles sont utilisées dans le langage F # pour comparer des données avec une ou plusieurs structures logiques, décomposer les données en parties constituantes ou extraire des informations à partir des données de différentes manières.


## <a name="remarks"></a>Remarques
Modèles utilisés dans de nombreuses constructions de langage, tels que le `match` expression. Ils sont utilisés lorsque vous traitez des arguments pour les fonctions dans `let` liaisons, des expressions lambda et les gestionnaires d’exceptions associés le `try...with` expression. Pour plus d’informations, consultez [Expressions de correspondance](match-expressions.md), [liaisons let](functions/let-bindings.md), [Expressions Lambda : le `fun` mot clé](functions/lambda-expressions-the-fun-keyword.md), et [Exceptions : le `try...with` Expression](exception-handling/the-try-with-expression.md).

Par exemple, dans le `match` expression, le *modèle* est ce qui suit le symbole de barre verticale.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Chaque modèle agit comme une règle transforme l’entrée d’une certaine façon. Dans la `match` expression, chaque modèle est examinée tour à tour pour voir si les données d’entrée sont compatibles avec le modèle. Si une correspondance est trouvée, l’expression de résultat est exécutée. Si une correspondance est introuvable, la règle de modèle suivante est testée. Le facultatif quand *condition* partie est expliquée dans [Expressions de correspondance](match-expressions.md).

Modèles pris en charge sont indiqués dans le tableau suivant. Au moment de l’exécution, l’entrée est testée par chacun des modèles dans l’ordre indiqué dans le tableau suivant et modèles sont appliquées de manière récursive, à partir de tout d’abord au dernier telles qu’elles apparaissent dans votre code et de gauche à droite pour les modèles sur chaque ligne.

|Nom|Description|Exemple|
|----|-----------|-------|
|Modèle de constante|Toute numérique, caractère, ou littéral de chaîne, une constante d’énumération ou identificateur littéral défini|`1.0`, `"test"`, `30`, `Color.Red`|
|Modèle d’identificateur|Valeur de cas d’une union discriminée, étiquette d’exception ou un cas de modèle actif|`Some(x)`<br /><br />`Failure(msg)`|
|Modèle de variable|*identifier*|`a`|
|`as`modèle|*modèle* comme *identificateur*|`(a, b) as tuple1`|
|OU un modèle|*Motif1* &#124; *Motif2*|<code>([h] &#124; [h; _])</code>|
|ET le modèle|*Motif1* &amp; *Motif2*|`(a, b) & (_, "test")`|
|Modèle Cons|*identificateur* :: *identificateur de la liste*|`h :: t`|
|Modèle de liste|[ *modèle_1*;... ; *modèle_n* ]|`[ a; b; c ]`|
|Modèle de tableau|[&#124; *modèle_1*;.. ; *modèle_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Modèle entre parenthèses|( *modèle* )|`( a )`|
|Modèle de tuple|( *modèle_1*,..., *modèle_n* )|`( a, b )`|
|Modèle d’enregistrement|{ *identificateur1* = *modèle_1*;... ; *identificateur_n* = *modèle_n* }|`{ Name = name; }`|
|Modèle de caractère générique|_|`_`|
|Modèle avec une annotation de type|*modèle* : *type*|`a : int`|
|Modèle de test de type|:? *type* [comme *identificateur* ]|`:? System.DateTime as dt`|
|Modèle Null|null|`null`|

## <a name="constant-patterns"></a>Modèles de constante
Modèles de constante sont numériques, les caractères et les littéraux de chaîne, des constantes d’énumération (avec le nom de type d’énumération inclus). A `match` expression qui comporte uniquement les modèles de constante peut être comparée à une instruction case dans d’autres langages. L’entrée est comparée à la valeur littérale et le modèle correspond à si les valeurs sont égales. Le type du littéral doit être compatible avec le type de l’entrée.

L’exemple suivant illustre l’utilisation de modèles de littéral et utilise également un modèle de variable et un modèle OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Un autre exemple de modèle de littéral est un modèle basé sur des constantes d’énumération. Vous devez spécifier le nom du type énumération lorsque vous utilisez des constantes d’énumération.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Modèles d’identificateur
Si le modèle est une chaîne de caractères qui forme un identificateur valide, le formulaire de l’identificateur détermine la façon dont le modèle est mis en correspondance. Si l’identificateur est supérieure à un caractère unique et commence par un caractère majuscule, le compilateur tente d’établir une correspondance avec le modèle d’identificateur. L’identificateur de ce modèle peut être une valeur marquée avec l’attribut littéral, un cas d’union discriminée, un identificateur d’exception ou un cas de modèle actif. Si aucun identificateur correspondant n’est trouvé, la correspondance échoue et la règle de modèle suivante, le modèle de variable, est comparée à l’entrée.

Les modèles d’union discriminées peuvent être simples nommé cas ou ils peuvent avoir une valeur ou un tuple contenant plusieurs valeurs. S’il existe une valeur, vous devez spécifier un identificateur pour la valeur. Dans le cas d’un tuple, vous devez fournir un modèle de tuple avec un identificateur pour chaque élément de tuple ou un identificateur avec un nom de champ pour un ou plusieurs champs de l’unions. Consultez les exemples de code dans cette section pour obtenir des exemples.

Le `option` type est une union discriminée qui a deux cas, `Some` et `None`. Un cas (`Some`) a une valeur, alors que l’autre (`None`) est simplement un cas nommé. Par conséquent, `Some` doit avoir une variable pour la valeur associée à la `Some` , mais `None` doit apparaître de lui-même. Dans le code suivant, la variable `var1` reçoit la valeur obtenue en mettant en correspondance à la `Some` cas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Dans l’exemple suivant, la `PersonName` union discriminée contient un mélange de chaînes et des caractères qui représentent des formes possibles de noms. Les cas de l’union discriminée sont `FirstOnly`, `LastOnly`, et `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Pour les unions discriminées qui ont des champs nommés, le signe égal (=) vous permet d’extraire la valeur d’un champ nommé. Par exemple, considérez une union discriminée avec une déclaration comme suit.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Vous pouvez utiliser les champs nommés dans une expression de correspondance de modèle comme suit.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

L’utilisation du champ nommé est facultative, de sorte que dans l’exemple précédent, les deux `Circle(r)` et `Circle(radius = r)` ont le même effet.

Lorsque vous spécifiez plusieurs champs, utilisez le point-virgule ( ;) comme séparateur.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Modèles actifs vous permettent de définir des critères spéciaux personnalisés plus complexes. Pour plus d’informations sur les modèles actifs, consultez [modèles actifs](active-patterns.md).

Le cas où l’identificateur est une exception est utilisé dans les critères spéciaux dans le contexte de gestionnaires d’exceptions. Pour plus d’informations sur la mise en correspondance dans la gestion des exceptions, consultez [Exceptions : le `try...with` Expression](exception-handling/the-try-with-expression.md).


## <a name="variable-patterns"></a>Modèles de variable
Le modèle de variable assigne la valeur correspondance à un nom de variable, qui est ensuite disponible pour une utilisation dans l’expression d’exécution à droite de la `->` symbole. Un modèle de variable seul correspond à n’importe quelle entrée, mais les modèles de variable apparaissent souvent dans d’autres modèles, par conséquent, l’activation des structures plus complexes telles que les tuples et les tableaux de manière à être décomposée en variables.

L’exemple suivant montre un modèle de variable dans un modèle de tuple.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>en tant que modèle
Le `as` modèle est un modèle qui a un `as` clause ajouté à la fin. Le `as` clause lie la valeur correspondante à un nom qui peut être utilisé dans l’expression de l’exécution d’un `match` expression, ou, dans le cas où ce modèle est utilisé dans un `let` de liaison, le nom est ajouté en tant qu’une liaison à la portée locale.

L’exemple suivant utilise une `as` modèle.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OU un modèle
Le modèle OR est utilisé lorsque les données d’entrée peuvent correspondre à plusieurs modèles, et que vous souhaitez exécuter le même code en conséquence. Les types des deux côtés du modèle OR doivent être compatibles.

L’exemple suivant illustre le modèle OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>ET le modèle
Le modèle AND requiert que l’entrée corresponde à deux modèles. Les types des deux côtés du modèle AND doivent être compatibles.

L’exemple suivant est semblable à `detectZeroTuple` indiqué dans le [Tuple modèle](https://msdn.microsoft.com/library/#tuple) section plus loin dans cette rubrique, mais ici `var1` et `var2` sont obtenus en tant que valeurs à l’aide du modèle AND.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Modèle Cons
Le modèle cons est utilisé pour décomposer une liste du premier élément, le *head*et une liste qui contient les éléments restants, le *fin*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Modèle de liste
Le modèle de liste permet la décomposition en un nombre d’éléments de listes. Le modèle de liste proprement dit peut faire correspondre uniquement les listes d’un nombre spécifique d’éléments.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Modèle de tableau
Le modèle de tableau est semblable au modèle de liste et peut être utilisé pour décomposer des tableaux de longueur spécifique.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Modèle entre parenthèses
Parenthèses peuvent être regroupés autour de modèles pour obtenir l’associativité désirée. Dans l’exemple suivant, les parenthèses sont utilisées pour contrôler l’associativité entre un modèle AND et un modèle cons.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Modèle de tuple
Le modèle de tuple correspond à entrée sous forme de tuple et permet le tuple à être décomposée en éléments constituants à l’aide de critères spéciaux de variables pour chaque position dans le tuple.

L’exemple suivant illustre le modèle de tuple et utilise également des modèles de littéral, modèles de variable et le modèle de caractère générique.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Modèle d’enregistrement
Le modèle d’enregistrement est utilisé pour décomposer des enregistrements pour extraire les valeurs des champs. Le modèle n’a pas référencer tous les champs de l’enregistrement. tous les champs omis ne participent pas mise en correspondance uniquement et ne sont pas extraites.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Modèle de caractère générique
Le modèle de caractère générique est représenté par un trait de soulignement (`_`) de caractères et correspond à aucune entrée, comme le modèle de variable, sauf que l’entrée est ignorée et non assigné à une variable. Le modèle de caractère générique est souvent utilisé dans d’autres modèles comme un espace réservé pour les valeurs qui ne sont pas nécessaires dans l’expression à droite de la `->` symbole. Le modèle de caractère générique est aussi fréquemment utilisé à la fin d’une liste de modèles pour correspondre à n’importe quelle entrée sans correspondance. Le modèle de caractère générique est illustré dans de nombreux exemples de code dans cette rubrique. Consultez le code précédent pour obtenir un exemple.


## <a name="patterns-that-have-type-annotations"></a>Modèles qui ont des Annotations de Type
Les modèles peuvent avoir des annotations de type. Ils se comportent comme d’autres annotations de type et guident l’inférence comme d’autres annotations de type. Entre parenthèses sont obligatoires autour des annotations de type dans les modèles. Le code suivant montre un modèle qui a une annotation de type.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Modèle de Test de type
Le modèle de test de type est utilisé pour faire correspondre l’entrée par rapport à un type. Si le type d’entrée est une recherche de correspondance (ou un type dérivé de) le type spécifié dans le modèle, la correspondance réussit.

L’exemple suivant illustre le modèle de test de type.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Modèle Null
Le modèle de valeur null correspond à la valeur null qui peut s’afficher lorsque vous travaillez avec des types qui autorisent une valeur null. Modèles null sont fréquemment utilisés lors de l’interaction avec du code .NET Framework. Par exemple, la valeur de retour d’une API .NET peut être entrée à un `match` expression. Vous pouvez contrôler le déroulement du programme selon si la valeur de retour est null et également sur d’autres caractéristiques de la valeur retournée. Vous pouvez utiliser le modèle null pour empêcher les valeurs null de se propager vers le reste de votre programme.

L’exemple suivant utilise le modèle null et le modèle de variable.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Voir aussi
[Expressions match](match-expressions.md)

[Modèles actifs](active-patterns.md)

[Informations de référence du langage F#](index.md)
