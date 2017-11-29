---
title: "Paramètres et arguments (F#)"
description: "En savoir plus sur F # prise en charge linguistique pour la définition de paramètres et de passer des arguments aux fonctions, des méthodes et propriétés."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9b37a5c4-9263-4513-822a-fbb0d1004254
ms.openlocfilehash: 50f54bacd9ba7ec20a7151794734f93200df9f2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="parameters-and-arguments"></a>Paramètres et arguments

Cette rubrique décrit la prise en charge de langage de définition de paramètres et de passer des arguments aux fonctions, des méthodes et propriétés. Il inclut des informations sur le passage par référence et comment définir et utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.


## <a name="parameters-and-arguments"></a>Paramètres et arguments
Le terme *paramètre* est utilisé pour décrire les noms des valeurs qui sont censées être fournies. Le terme *argument* est utilisé pour les valeurs fournies pour chaque paramètre.

Paramètres peuvent être spécifiés sous forme de tuple ou curryfiés, ou dans une combinaison des deux. Vous pouvez passer des arguments à l’aide d’un nom de paramètre explicite. Les paramètres des méthodes peuvent être spécifiés comme étant facultatifs et une valeur par défaut.


## <a name="parameter-patterns"></a>Modèles de paramètre
En règle générale, les paramètres fournis à des fonctions et méthodes sont des modèles séparés par des espaces. Cela signifie que, en principe, les modèles décrits dans [Expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.

Les méthodes utilisent généralement la forme de tuple de passage d’arguments. Cela permet d’obtenir un résultat plus clair de la perspective d’autres langages .NET, car la forme de tuple correspond à la façon d’arguments sont passés dans les méthodes .NET.

Le formulaire curryfié est souvent utilisé avec des fonctions créées à l’aide de `let` liaisons.

Le pseudo-code suivant montre des exemples de tuple et d’arguments curryfiés.

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

Combiner les formes sont possibles lorsque certains arguments sont dans des tuples et que certains ne sont pas.

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

Autres modèles peuvent également servir dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il peut être une correspondance incomplète au moment de l’exécution. L’exception `MatchFailureException` est généré lorsque la valeur d’un argument ne correspond pas les modèles spécifiés dans la liste de paramètres. Le compilateur émet un avertissement lorsqu’un modèle de paramètre accepte des correspondances incomplètes. Au moins un autre modèle est souvent utile pour les listes de paramètres, et qui est le modèle de caractère générique. Vous utilisez le modèle de caractère générique dans une liste de paramètres lorsque vous souhaitez simplement ignorer tous les arguments sont fournis. Le code suivant illustre l’utilisation du modèle de caractère générique dans une liste d’arguments.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

Le modèle de caractère générique peut être utile chaque fois que vous n’avez pas besoin des arguments transmis, comme dans le point d’entrée principal à un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande fournis normalement en tant que tableau de chaînes, comme dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

Autres modèles sont parfois utilisées dans les arguments sont les `as` modèle et les modèles d’identificateur associés aux unions discriminées et les modèles actifs. Vous pouvez utiliser le modèle d’union discriminée seul cas comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

La sortie est la suivante.

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

Modèles actifs peuvent être utiles en tant que paramètres, par exemple, lors de la transformation d’un argument en un format de votre choix, comme dans l’exemple suivant :

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

Vous pouvez utiliser la `as` modèle pour stocker une valeur correspondante comme valeur locale, comme indiqué dans la ligne de code suivante.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

Un autre modèle utilisé parfois est une fonction qui laisse le dernier argument sans nom en fournissant, en tant que le corps de la fonction, une expression lambda qui exécute immédiatement une correspondance de modèle sur l’argument implicite. Ceci est la ligne de code suivante.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

Ce code définit une fonction qui accepte une liste générique et retourne `true` si la liste est vide, et `false` dans le cas contraire. L’utilisation de ces techniques permettre rendre le code plus difficile à lire.

Parfois, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes dans votre programme ont uniquement trois éléments, vous pouvez utiliser un modèle semblable à la suivante dans une liste de paramètres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

L’utilisation de modèles qui ont des correspondances incomplètes est mieux réservée pour une création rapide de prototypes et d’autres utilisations temporaires. Le compilateur émet un avertissement pour ce code. Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et par conséquent ne conviennent pas aux API de composant.

## <a name="named-arguments"></a>Arguments nommés
Les arguments de méthodes peuvent être spécifiés par position dans une liste d’arguments séparée par des virgules, ou passés explicitement à une méthode en fournissant le nom, suivi par un signe égal et la valeur à passer dans. S’il est spécifié en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.

Arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications dans l’API, telles que la réorganisation des paramètres de méthode.

Arguments nommés sont autorisés uniquement pour les méthodes, pas pour `let`-lié des fonctions, des valeurs de fonction ou des expressions lambda.

L’exemple de code suivant illustre l’utilisation d’arguments nommés.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe à l’aide d’une syntaxe similaire à celle des arguments nommés. L’exemple suivant illustre cette syntaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Pour plus d’informations, consultez [constructeurs (F #)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).

## <a name="optional-parameters"></a>Paramètres facultatifs
Vous pouvez spécifier un paramètre facultatif pour une méthode à l’aide d’un point d’interrogation devant le nom du paramètre. Paramètres facultatifs sont interprétés comme le type d’option F #, vous pouvez les interroger normalement que les types d’options sont interrogées à l’aide un `match` expression avec `Some` et `None`. Paramètres facultatifs sont autorisés uniquement sur les membres, et non sur les fonctions créées à l’aide de `let` liaisons.

Vous pouvez également utiliser une fonction `defaultArg`, qui définit une valeur par défaut d’un argument facultatif. Le `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut en tant que la seconde.

L’exemple suivant illustre l’utilisation des paramètres optionnels.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

La sortie est la suivante.

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>Le passage par référence
F # prend en charge le `byref` mot clé, qui spécifie qu’un paramètre est passé par référence. Cela signifie que toute modification apportée à la valeur est conservées après l’exécution de la fonction. Les valeurs fournies pour un `byref` paramètre doit être mutable. Vous pouvez également passer des cellules de référence du type approprié.

Passage par référence dans les langages .NET est devenu un moyen de retourner plusieurs valeurs à partir d’une fonction. En F #, vous pouvez retourner un tuple à cette fin, ou utiliser une cellule de référence mutable en tant que paramètre. Le `byref` paramètre est fourni principalement pour l’interopérabilité avec les bibliothèques .NET.

Les exemples suivants illustrent l’utilisation de la `byref` (mot clé). Notez que lorsque vous utilisez une cellule de référence en tant que paramètre, vous devez créer une cellule de référence comme valeur nommée et utiliser comme paramètre, non seulement ajouter la `ref` opérateur, comme indiqué dans le premier appel à `Increment` dans le code suivant. Étant donné que la création d’une cellule de référence crée une copie de la valeur sous-jacente, le premier appel incrémente simplement une valeur temporaire.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

Vous pouvez utiliser un tuple comme valeur de retour pour stocker les `out` paramètres dans les méthodes de bibliothèque .NET. Vous pouvez également traiter les `out` paramètre comme un `byref` paramètre. L’exemple de code suivant illustre deux façons.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>Tableaux de paramètres
Il est parfois nécessaire de définir une fonction qui accepte un nombre arbitraire de paramètres de type hétérogène. Il ne serait pas pratique de créer toutes les méthodes surchargées possibles pour prendre en compte pour tous les types qui peuvent être utilisées. Les implémentations .NET prennent en charge ces méthodes via la fonctionnalité de tableau de paramètres. Une méthode qui prend un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres. Les paramètres sont placés dans un tableau. Le type des éléments du tableau détermine les types de paramètres qui peuvent être passés à la fonction. Si vous définissez le tableau de paramètres avec `System.Object` comme type d’élément, puis le code client peut passer des valeurs de n’importe quel type.

En F #, les tableaux de paramètres peuvent uniquement être définies dans les méthodes. Ils ne peut pas être utilisés dans des fonctions autonomes ou des fonctions qui sont définies dans des modules.

Vous définissez un tableau de paramètres à l’aide de la `ParamArray` attribut. Le `ParamArray` attribut ne peut être appliqué qu’au dernier paramètre.

Le code suivant illustre l’appel à une méthode .NET qui prend un tableau de paramètres et de la définition d’un type en F # qui a une méthode qui prend un tableau de paramètres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

Lors de l’exécution dans un projet, la sortie du code précédent est comme suit :

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>Voir aussi
[Membres](members/index.md)
