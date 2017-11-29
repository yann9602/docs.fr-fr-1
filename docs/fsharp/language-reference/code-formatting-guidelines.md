---
title: Indications pour la mise en forme du code (F#)
description: "Découvrez les instructions de mise en forme de mise en retrait code pour le langage de programmation pour une meilleure lisibilité, esthétique, la normalisation et la compilation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3f79717c-f84e-448d-9ce4-90e40a644ba1
ms.openlocfilehash: cc56c67f356b99defd8dc28770f87be1f58443c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="code-formatting-guidelines"></a>Indications pour la mise en forme du code

Cette rubrique résume les instructions de mise en retrait de code pour F #. Étant donné que le langage F # est sensible aux sauts de ligne et de mise en retrait, il n’est pas simplement une question de lisibilité, esthétique ou le codage normalisation problème pour mettre correctement en forme votre code. Vous devez mettre en forme votre code correctement pour qu’il se compile correctement.


## <a name="general-rules-for-indentation"></a>Règles générales pour la mise en retrait
Lors de la mise en retrait est requise, vous devez utiliser des espaces, tabulations pas. Au moins un espace est requis. Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait est typique. Vous pouvez configurer Visual Studio en fonction des normes de mise en retrait de votre organisation en modifiant les options de la `Options` boîte de dialogue, qui est disponible à partir de la `Tools` menu. Dans le `Text Editor` nœud, développez `F#` puis cliquez sur `Tabs`. Pour obtenir une description des options disponibles, consultez [Options, éditeur de texte, tous les langages, onglets](https://msdn.microsoft.com/library/7sffa753.aspx).

En règle générale, lorsque le compilateur analyse votre code, il conserve une pile interne qui indique le niveau d’imbrication actuel. Lorsque le code est mis en retrait, un nouveau niveau d’imbrication est créé, ou cette pile interne. Lorsqu’une construction se termine, le niveau est dépilé. Mise en retrait est un moyen pour signaler la fin d’un niveau et de dépiler la pile interne, mais certains jetons provoquent également le niveau d’être dépilés, telles que le `end` (mot clé), ou d’une accolade fermante ou une parenthèse.

Le code dans une construction multiligne, comme une définition de type, définition de fonction, `try...with` construction et constructions de bouclage, doivent être mis en retrait par rapport à la ligne d’ouverture de la construction. La première ligne mise en retrait établit une position de colonne pour le code suivant dans la même construction. Le niveau de mise en retrait est appelé un *contexte*. La position de colonne définit une colonne minimale, appelée un *ligne hors-jeu*, pour les lignes de code qui se trouvent dans le même contexte. Lorsqu’une ligne de code est rencontrée, qui est mis en retrait inférieure à la position de colonne établie, le compilateur suppose que le contexte est terminée et que vous codez maintenant au niveau suivant, dans le contexte précédent. Le terme *hors-jeu* est utilisé pour décrire la condition dans laquelle une ligne de code déclenche la fin d’une construction, car elle n’est pas suffisamment mise en retrait. En d’autres termes, le code à gauche d’une ligne hors-jeu est hors-jeu. Dans le code mis en retrait correctement, vous tirer parti de la règle de hors-jeu afin de définir la fin de constructions. Si vous utilisez incorrectement mise en retrait, une condition de hors-jeu peut contraindre le compilateur à émettre un avertissement ou peut provoquer l’interprétation incorrecte de votre code.

Lignes hors-jeu sont déterminées comme suit.


- Un `=` jeton associé à un `let` introduit une ligne hors-jeu au niveau de la colonne du premier jeton après le `=` signe.


- Dans un `if...then...else` expression, la position de colonne du premier jeton après le `then` mot clé ou le `else` mot clé introduit une ligne hors-jeu.


- Dans un `try...with` expression, le premier jeton après `try` introduit une ligne hors-jeu.


- Dans un `match` expression, le premier jeton après `with` et le premier jeton après chaque `->` introduisent des lignes hors-jeu.


- Le premier jeton après `with` dans un type d’extension introduit une ligne hors-jeu.


- Le premier jeton après une accolade ouvrante ou une parenthèse, ou après le `begin` (mot clé), introduit une ligne hors-jeu.


- Le premier caractère dans les mots clés `let`, `if`, et `module` introduisent des lignes hors-jeu.


Les exemples de code suivants illustrent les règles de mise en retrait. Ici, les instructions print s’appuient sur la mise en retrait pour les associer avec le contexte approprié. Chaque fois que la mise en retrait est décalé vers, le contexte est dépilé et retourne au contexte précédent. Par conséquent, un espace est imprimé à la fin de chaque itération ; « Terminé » ! est imprimé uniquement une seule fois, car la mise en retrait hors-jeu établit qu’il n’est pas partie de la boucle. L’impression de la chaîne « Contexte de niveau supérieur » ne fait pas partie de la fonction. Par conséquent, il est imprimé en premier lieu, pendant l’initialisation statique, avant que la fonction est appelée.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

La sortie est la suivante.

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

Lorsque vous vous arrêtez les longues lignes, la continuation de la ligne doit être plus en retrait la construction englobante. Par exemple, les arguments de fonction doivent être plus en retrait le premier caractère du nom de fonction, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

Il existe des exceptions à ces règles, comme décrit dans la section suivante.


## <a name="indentation-in-modules"></a>Mise en retrait dans les Modules
Code dans un module local doit être mis en retrait par rapport au module, mais le code dans un module de niveau supérieur ne doit pas être mis en retrait. Les éléments Namespace n’ont pas à être mis en retrait.

Les exemples de code suivants illustrent ce principe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

Pour plus d’informations, consultez [Modules](modules.md).


## <a name="exceptions-to-the-basic-indentation-rules"></a>Exceptions aux règles de mise en retrait de base
La règle générale, comme décrit dans la section précédente, est que code dans les constructions multilignes doit être mis en retrait par rapport à la mise en retrait de la première ligne de la construction, et que la fin de la construction est déterminée par lors de la première ligne hors-jeu se produit. Une exception à la règle lorsque la fin de contextes est que certaines constructions, telles que la `try...with` expression, le `if...then...else` expression et l’utilisation de `and` syntaxe de déclaration mutuellement les fonctions récursives ou types, de plusieurs parties. Vous mettez en retrait les dernières parties, telles que `then` et `else` dans un `if...then...else` expression, au même niveau que le jeton qui démarre l’expression, mais au lieu d’indiquer une fin au contexte, il représente la partie suivante du même contexte. Par conséquent, un `if...then...else` expression peut être écrite comme dans l’exemple de code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

L’exception à la règle de hors-jeu s’applique uniquement à la `then` et `else` mots clés. Par conséquent, même s’il n’est pas une erreur pour mettre en retrait le `then` et `else` davantage, ne peut pas mettre en retrait les lignes de code dans un `then` bloc génère un avertissement. Ceci est illustré dans les lignes de code suivantes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

Pour le code dans un `else` bloc, une règle spéciale supplémentaire s’applique. L’avertissement dans l’exemple précédent se produit uniquement sur le code dans le `then` blocs, pas sur le code dans le `else` bloc. Cela vous permet d’écrire du code qui vérifie différentes conditions au début d’une fonction sans forcer le reste du code pour la fonction, ce qui peut être dans un `else` bloc, d’être mises en retrait. Par conséquent, vous pouvez écrire ce qui suit sans générer d’avertissement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

Une autre exception à la règle de contextes se terminent lorsqu’une ligne n’est pas mise en retrait comme une ligne précédente est tel que pour les opérateurs infix `+` et `|>`. Les lignes qui commencent par les opérateurs infixes sont autorisées à commencer `(1 + oplength)` colonnes avant la position normale, sans déclencher la fin du contexte, où `oplength` est le nombre de caractères qui composent l’opérateur. Ainsi, le premier jeton après l’opérateur pour les aligner avec la ligne précédente.

Par exemple, dans le code suivant, le `+` symbole est autorisé à être mis en retrait de deux colonnes inférieur à la ligne précédente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

Bien que la mise en retrait augmente généralement à mesure que le niveau d’imbrication supérieur, il existe plusieurs constructions dans lequel le compilateur vous permet de réinitialiser la mise en retrait à une position de colonne inférieure.

Les constructions qui autorisent une réinitialisation de position de colonne sont les suivantes :


- Corps de fonctions anonymes. Dans le code suivant, l’expression print commence à une position de colonne qui est plue à gauche que le `fun` (mot clé). Toutefois, la ligne ne doit pas commencer à une colonne à gauche du début du niveau de mise en retrait précédent (autrement dit, à gauche de la `L` dans `List`).
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- Constructions entre parenthèses ou entre `begin` et `end` dans un `then` ou `else` bloquer d’un `if...then...else` fourni d’expression, la mise en retrait n’est pas inférieure à la position de colonne de la `if` (mot clé). Cette exception autorise un style de programmation dans lequel une parenthèse ouvrante ou `begin` est utilisé à la fin d’une ligne après `then` ou `else`.


- Corps des modules, des classes, des interfaces et des structures délimités par `begin...end`, `{...}`, `class...end`, ou `interface...end`. Cela permet à un style dans lequel le mot clé d’ouverture d’une définition de type peut être sur la même ligne que le nom de type sans forcer le corps entier à être mis en retrait soulevez-la le mot clé d’ouverture.
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
