---
title: "Fonctions comme valeurs de première classe (F#)"
description: "Découvrez comment les fonctions sont élevées à l’état de première classe dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a>Fonctions comme valeurs de première classe

Une caractéristique essentielle de langages de programmation fonctionnelle est l’élévation des fonctions à l’état de première classe. Vous devez être en mesure de faire avec une fonction tout ce que vous pouvez faire avec les valeurs des autres types intégrés et être en mesure de le faire avec un degré comparable d’effort.

Les mesures courantes de l’état de première classe sont les suivantes :

- Vous liez des fonctions à des identificateurs ? Autrement dit, pouvez vous donner les noms ?

- Peut stocker les fonctions dans les structures de données, comme dans une liste ?

- Vous passez une fonction en tant qu’argument dans un appel de fonction ?

- Peut retourner d’une fonction à partir d’un appel de fonction ?

Les deux dernières mesures définissent ce que l'on appelle *opérations d’ordre supérieur* ou *fonctions d’ordre supérieur*. Fonctions d’ordre supérieur acceptent des fonctions en tant qu’arguments et retournent des fonctions en tant que la valeur d’appels de fonction. Ces opérations prennent en charge ces éléments de la programmation fonctionnelle que le mappage des fonctions et la composition de fonctions.


## <a name="give-the-value-a-name"></a>Donnez un nom à la valeur

Si une fonction est une valeur de première classe, vous devez être en mesure de nom, tout comme vous pouvez nommer les entiers, chaînes et autres types intégrés. Il s’agit de programmation fonctionnelle comme un identificateur de liaison à une valeur. F # utilise [ `let` liaisons](../language-reference/functions/let-bindings.md) pour lier des noms à des valeurs : `let <identifier> = <value>`. Le code suivant montre deux exemples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Vous pouvez nommer une fonction aussi facilement. L’exemple suivant définit une fonction nommée `squareIt` par l’identificateur de liaison `squareIt` à la [expression lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. Fonction `squareIt` possède un paramètre, `n`, et elle retourne le carré de ce paramètre.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # fournit une syntaxe plus concise pour obtenir le même résultat avec moins de saisie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

Les exemples qui suivent généralement utilisent le premier style `let <function-name> = <lambda-expression>`, mettre en évidence les similitudes entre la déclaration de fonctions et la déclaration d’autres types de valeurs. Toutefois, toutes les fonctions nommées peuvent également être écrites avec la syntaxe concise. Certains exemples sont écrits dans les deux sens.


## <a name="store-the-value-in-a-data-structure"></a>Stockez la valeur dans une Structure de données

Une valeur de première classe peut être stockée dans une structure de données. Le code suivant présente des exemples qui stockent des valeurs dans les listes et des tuples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Pour vérifier qu’un nom de fonction stocké dans un tuple a en fait la valeur d’une fonction, l’exemple suivant utilise le `fst` et `snd` opérateurs pour extraire les éléments de la première et deuxième tuple `funAndArgTuple`. Le premier élément dans le tuple est `squareIt` et le deuxième élément est `num`. Identificateur `num` est lié dans un précédent exemple à l’entier 10, un argument valide pour le `squareIt` (fonction). La deuxième expression applique le premier élément dans le tuple au deuxième élément dans le tuple : `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Tout comme l’identificateur `num` et de la valeur entière 10 peut être utilisés indifféremment, peuvent également identificateur `squareIt` et une expression lambda `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>Passez la valeur en tant qu’Argument

Si une valeur a un état de première classe dans une langue, vous pouvez le passer en tant qu’argument à une fonction. Par exemple, il est fréquent de passer des entiers et des chaînes en tant qu’arguments. Le code suivant montre des entiers et les chaînes passées comme arguments en F #.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

Si les fonctions ont l’état de première classe, vous devez être en mesure de les passer en tant qu’arguments de la même façon. N’oubliez pas qu’il s’agit de la première caractéristique des fonctions d’ordre supérieur.

Dans l’exemple suivant, la fonction `applyIt` possède deux paramètres, `op` et `arg`. Si vous envoyez une fonction qui a un paramètre pour `op` et un argument approprié pour la fonction `arg`, la fonction retourne le résultat de l’application `op` à `arg`. Dans l’exemple suivant, l’argument de fonction et l’argument entier sont envoyées de la même manière, à l’aide de leurs noms.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

La capacité d’envoyer une fonction en tant qu’argument à une autre fonction sous-jacente abstractions communes dans les langages de programmation fonctionnelle, telles que les opérations de mappage ou de filtrage. Une opération de mappage, par exemple, est une fonction d’ordre supérieur qui capture le calcul partagé par les fonctions dans une liste, effectuer une opération sur chaque élément, puis retournent une liste des résultats. Vous pourriez modifier chaque élément d’une liste de chaînes en majuscules pour incrémenter chaque élément dans une liste d’entiers ou au carré chaque élément. La partie erreurs du calcul est le processus récursive qui parcourt la liste et génère la liste des résultats à retourner. Cette partie est capturée dans la fonction de mappage. Il vous suffit d’écrire pour une application particulière est la fonction que vous souhaitez appliquer individuellement à chaque élément de liste (ajout, mise au carré, de changement de casse). Cette fonction est envoyée en tant qu’argument à la fonction de mappage, tout comme `squareIt` est envoyé à `applyIt` dans l’exemple précédent.

F # fournit des méthodes de mappage pour la plupart des types de collection, notamment [répertorie](../language-reference/lists.md), [tableaux](../language-reference/arrays.md), et [séquences](../language-reference/sequences.md). Les exemples suivants utilisent des listes. La syntaxe est `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Pour plus d’informations, consultez [répertorie](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Retourner la valeur d’un appel de fonction

Enfin, si une fonction a un état de première classe dans une langue, vous devez être en mesure de renvoyer la valeur d’un appel de fonction, tout comme vous retournez d’autres types, tels que les entiers et les chaînes.

Les appels de fonction suivants retournent des entiers et les affichent.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

L’appel de fonction suivant retourne une chaîne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

L’appel de fonction suivant, déclaré inline, retourne une valeur booléenne. La valeur affichée est `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

La possibilité de retourner une fonction en tant que la valeur d’un appel de fonction est la deuxième caractéristique des fonctions d’ordre supérieur. Dans l’exemple suivant, `checkFor` est défini comme une fonction qui accepte un seul argument, `item`et retourne une nouvelle fonction en tant que sa valeur. La fonction retournée prend une liste comme argument, `lst`et recherche `item` dans `lst`. Si `item` est présent, la fonction retourne `true`. Si `item` n’est pas présent, la fonction retourne `false`. Comme dans la section précédente, le code suivant utilise une fonction de la liste fournie, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), pour rechercher dans la liste.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Le code suivant utilise `checkFor` pour créer une nouvelle fonction qui accepte un seul argument, une liste et recherche 7 dans la liste.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

L’exemple suivant utilise l’état de première classe de fonctions en F # pour déclarer une fonction, `compose`, qui retourne une composition de deux arguments de fonction.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
Pour obtenir une version encore plus courte, consultez la section suivante, « Fonctions curryfiées. »


Le code suivant envoie deux fonctions en tant qu’arguments à `compose`, à la fois de qui acceptent un argument unique du même type. La valeur de retour est une nouvelle fonction qui est une composition de deux arguments de fonction.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F # fournit deux opérateurs, `<<` et `>>`, qui composent les fonctions. Par exemple, `let squareAndDouble2 = doubleIt << squareIt` est équivalente à `let squareAndDouble = compose doubleIt squareIt` dans l’exemple précédent.

L’exemple de retour d’une fonction en tant que la valeur d’un appel de fonction suivant crée un jeu d’estimation simple. Pour créer un jeu, appelez `makeGame` avec la valeur que vous voulez que quelqu'un deviner envoyé pour `target`. La valeur de retour de fonction `makeGame` est une fonction qui prend un argument (l’estimation) et indique si l’estimation est correcte.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Le code suivant appelle `makeGame`, envoi de la valeur `7` pour `target`. Identificateur `playGame` est lié à l’expression lambda retournée. Par conséquent, `playGame` est une fonction qui prend comme argument une seule valeur pour `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>Fonctions curryfiées

La plupart des exemples dans la section précédente peuvent être écrites plus concise en tirant parti des implicite *curryfication* dans les déclarations de fonction F #. Curryfication est un processus qui transforme une fonction qui a plusieurs paramètres dans une série de fonctions intégrées, chacune ayant un seul paramètre. En F #, les fonctions qui ont plusieurs paramètres sont intrinsèquement curryfiées. Par exemple, `compose` à partir de la section précédente peut être écrit comme indiqué dans le style concis suivant, avec trois paramètres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Toutefois, le résultat est une fonction d’un paramètre qui retourne une fonction d’un paramètre, qui à son tour retourne une autre fonction d’un paramètre, comme indiqué dans `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Vous pouvez accéder à cette fonction de plusieurs façons. Chacun des exemples suivants retourne et affiche 18. Vous pouvez remplacer `compose4` avec `compose4curried` dans chacun des exemples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Pour vérifier que la fonction continue à fonctionner comme avant, réessayez les cas de test d’origine.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
Vous pouvez limiter la curryfication en englobant les paramètres dans les tuples. Pour plus d’informations, consultez « Paramètre modèles » dans [paramètres et Arguments](../language-reference/parameters-and-arguments.md).

L’exemple suivant utilise la curryfication implicite pour écrire une version plus courte de `makeGame`. Les détails de `makeGame` construit et retourne le `game` (fonction) sont moins explicite dans ce format, mais vous pouvez vérifier à l’aide de cas de test d’origine que le résultat est le même.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Pour plus d’informations sur la curryfication, consultez « Application partielle d’Arguments » dans [fonctions](../language-reference/functions/index.md).


## <a name="identifier-and-function-definition-are-interchangeable"></a>Identificateur et la définition de fonction sont interchangeables
Le nom de variable `num` dans les précédents exemples a la valeur entière 10 et il n’est pas surprenant dans laquelle `num` est valide, 10 est également valide. Est de même des identificateurs de fonction et leurs valeurs : partout où le nom de la fonction peut être utilisé, l’expression lambda à laquelle il est lié peut être utilisée.

L’exemple suivant définit un `Boolean` fonction appelée `isNegative`et utilise ensuite le nom de la fonction et la définition de la fonction de manière interchangeable. Les trois exemples suivants retournent et affichent tous `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Pour mettre une étape supplémentaire, la valeur de remplacement qui `applyIt` lié à pour `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Les fonctions sont des valeurs de première classe en F # #

Les exemples dans les sections précédentes montrent que les fonctions F # satisfont les critères de valeurs de première classe en F #:

- Vous pouvez lier un identificateur à une définition de fonction.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Vous pouvez stocker une fonction dans une structure de données.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Vous pouvez passer une fonction en tant qu’argument.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Vous pouvez retourner une fonction en tant que la valeur d’un appel de fonction.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Pour plus d’informations sur F #, consultez le [référence du langage F #](../language-reference/index.md).

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Le code suivant contient tous les exemples dans cette rubrique.

### <a name="code"></a>Code

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>Voir aussi

[Listes](../language-reference/lists.md)

[Tuples](../language-reference/tuples.md)

[Fonctions](../language-reference/functions/index.md)

[`let`Liaisons](../language-reference/functions/let-bindings.md)

[Expressions lambda : Le `fun` (mot clé)](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
