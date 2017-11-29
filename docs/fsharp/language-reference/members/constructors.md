---
title: Constructeurs (F#)
description: "Découvrez comment définir et utiliser des constructeurs dans F # pour créer et initialiser des objets de classe ou structure."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a>Constructeurs

Cette rubrique décrit comment définir et utiliser les constructeurs pour créer et initialiser des objets de classe ou structure.


## <a name="construction-of-class-objects"></a>Construction d’objets de classe
Les objets de types de classe ont des constructeurs. Il existe deux types de constructeurs. Un est le constructeur principal, dont les paramètres apparaissent entre parenthèses juste après le nom de type. Spécifiez d’autres, facultatifs des constructeurs supplémentaires à l’aide de la `new` (mot clé). Ces constructeurs supplémentaires doivent appeler le constructeur principal.

Le constructeur principal contient `let` et `do` les liaisons qui apparaissent au début de la définition de classe. A `let` liaison déclare des champs privés et les méthodes de la classe ; un `do` liaison exécute du code. Pour plus d’informations sur `let` liaisons dans les constructeurs de classe, consultez [ `let` liaisons dans les Classes](let-bindings-in-classes.md). Pour plus d’informations sur `do` liaisons dans les constructeurs, consultez [ `do` liaisons dans les Classes](do-bindings-in-classes.md).

Que le constructeur à appeler soit un constructeur principal ou un constructeur supplémentaire, vous pouvez créer des objets en utilisant un `new` expression, avec ou sans le paramètre facultatif `new` (mot clé). Vous initialisez vos objets avec des arguments de constructeur, soit en répertoriant les arguments dans l’ordre et séparés par des virgules et mise entre parenthèses, ou à l’aide des arguments nommés et des valeurs entre parenthèses. Vous pouvez également définir des propriétés sur un objet lors de la construction de l’objet en utilisant les noms de propriété et assigner des valeurs comme arguments de constructeur nommés.

Le code suivant illustre une classe qui a un constructeur et différentes façons de créer des objets.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

La sortie est la suivante.

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Construction de Structures
Les structures respectent toutes les règles de classes. Par conséquent, vous pouvez avoir un constructeur principal, et vous pouvez fournir des constructeurs supplémentaires à l’aide de `new`. Toutefois, il existe une différence importante entre les structures et classes : structures peuvent avoir un constructeur par défaut (autrement dit, un sans argument) même si aucun constructeur principal n’est définie. Le constructeur par défaut initialise tous les champs à la valeur par défaut pour ce type, généralement zéro ou à son équivalent. Tous les constructeurs que vous définissez pour des structures doivent avoir au moins un argument afin qu’ils ne sont pas en conflit avec le constructeur par défaut.

En outre, les structures ont souvent des champs qui sont créés à l’aide de la `val` mot-clé ; classes peuvent également avoir ces champs. Structures et classes qui ont des champs définis à l’aide de la `val` (mot clé) peut également être initialisée dans des constructeurs supplémentaires à l’aide d’expressions d’enregistrement, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Pour plus d’informations, consultez [champs explicites : le `val` mot clé](explicit-fields-the-val-keyword.md).


## <a name="executing-side-effects-in-constructors"></a>Exécution d’effets secondaires dans les constructeurs
Un constructeur principal dans une classe peut exécuter du code dans un `do` liaison. Toutefois, que se passe-t-il si vous devez exécuter du code dans un constructeur supplémentaire sans un `do` liaison ? Pour ce faire, vous utilisez la `then` (mot clé).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Les effets secondaires du constructeur principal est toujours exécuter. Par conséquent, la sortie est comme suit.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Auto-identificateurs dans les constructeurs
Dans d’autres membres, vous fournissez un nom pour l’objet actuel dans la définition de chaque membre. Vous pouvez également placer l’auto-identificateur sur la première ligne de la définition de classe à l’aide de la `as` (mot clé) immédiatement après les paramètres du constructeur. L’exemple suivant illustre cette syntaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Dans les constructeurs supplémentaires, vous pouvez également définir un auto-identificateur en plaçant le `as` clause juste après les paramètres du constructeur. L’exemple suivant illustre cette syntaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Des problèmes peuvent survenir lorsque vous essayez d’utiliser un objet avant d’être entièrement définie. Par conséquent, les utilisations de l’auto-identificateur peuvent provoquer le compilateur émet un avertissement et d’insérer des contrôles supplémentaires pour vérifier que les membres d’un objet ne sont pas accessibles avant l’initialisation de l’objet. Vous devez utiliser uniquement l’auto-identificateur dans le `do` liaisons du constructeur principal, ou après le `then` mot clé dans des constructeurs supplémentaires.

Le nom de l’auto-identificateur ne dispose pas être `this`. Il peut être n’importe quel identificateur valid.


## <a name="assigning-values-to-properties-at-initialization"></a>Assigner des valeurs aux propriétés lors de l’initialisation
Vous pouvez assigner des valeurs aux propriétés d’un objet de classe dans le code d’initialisation en ajoutant une liste d’assignations sous la forme `property = value` à la liste d’arguments pour un constructeur. Ceci est illustré dans l’exemple de code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

La version suivante du code précédent illustre la combinaison d’arguments ordinaires, les arguments facultatifs et les paramètres de propriété dans un appel de constructeur.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>Constructeurs de classe héritée
Lorsque vous héritez d’une classe de base qui a un constructeur, vous devez spécifier ses arguments dans la clause d’héritage. Pour plus d’informations, consultez [constructeurs et héritage](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Constructeurs statiques ou des constructeurs de Type
En plus de spécifier le code de création d’objets, statiques `let` et `do` liaisons peuvent être créées dans des types de classe qui s’exécutent avant que le type est tout d’abord utilisé pour effectuer l’initialisation au niveau du type. Pour plus d’informations, consultez [ `let` liaisons dans les Classes](let-bindings-in-classes.md) et [ `do` liaisons dans les Classes](do-bindings-in-classes.md).

## <a name="see-also"></a>Voir aussi
[Membres](index.md)
