---
title: Liaisons let (F#)
description: "Découvrez comment utiliser une liaison qui associe un identificateur à une valeur ou une fonction ' let' F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a>Liaisons let

A *liaison* associe un identificateur à une valeur ou une fonction. Vous utilisez la `let` (mot clé) pour lier un nom à une valeur ou une fonction.

## <a name="syntax"></a>Syntaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Remarques

Le `let` mot clé est utilisé dans des expressions pour définir des valeurs ou des valeurs de fonction pour un ou plusieurs noms de liaison. La forme la plus simple du `let` expression lie un nom à une valeur simple, comme suit.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Si vous séparez l’expression de l’identificateur à l’aide d’une nouvelle ligne, vous devez mettre en retrait chaque ligne de l’expression, comme dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Au lieu de simplement un nom, un modèle qui contient les noms peut être spécifié, par exemple, un tuple, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

Le *expression de corps* est l’expression dans laquelle les noms sont utilisés. L’expression de corps apparaît sur sa propre ligne, mise en retrait de ligne exactement avec le premier caractère dans le `let` (mot clé) :

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` liaison peut apparaître au niveau du module, dans la définition d’un type de classe, ou dans des portées locales, par exemple dans une définition de fonction. A `let` liaison de haut niveau dans un module ou d’un type de classe n’a pas besoin d’avoir une expression de corps, mais à d’autres niveaux de portée, l’expression de corps est obligatoire. Les noms liés sont utilisables après le point de définition, mais pas à tout moment avant le `let` liaison s’affiche, comme cela est illustré dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a>Liaisons de fonction

Liaisons de fonction suivent les règles pour les liaisons de valeur, à ceci près que les liaisons de fonction incluent le nom de fonction et les paramètres, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

En règle générale, les paramètres sont des modèles, tels que d’un modèle de tuple :

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` expression de liaison prend la valeur de la dernière expression. Par conséquent, dans l’exemple de code suivant, la valeur de `result` est calculée à partir de `100 * function3 (1, 2)`, qui prend la valeur `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Pour plus d’informations, consultez [Fonctions](index.md).

## <a name="type-annotations"></a>Annotations de type

Vous pouvez spécifier les types des paramètres en incluant un signe deux-points ( :) suivi d’un nom de type, le tout entre parenthèses. Vous pouvez également spécifier le type de la valeur de retour en ajoutant le signe deux-points et le type après le dernier paramètre. Les annotations de type complète pour `function1`, avec des entiers comme types de paramètres, se présente comme suit.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Lorsqu’il n’y a aucun paramètre de type explicite, l’inférence de type est utilisé pour déterminer les types de paramètres de fonctions. Cela peut inclure la généralisation automatique du type d’un paramètre générique.

Pour plus d’informations, consultez [généralisation automatique](../generics/automatic-generalization.md) et [l’inférence de Type](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Liaisons let dans des classes

A `let` liaison peut apparaître dans un type de classe, mais pas dans une structure ou un type d’enregistrement. Pour utiliser une liaison let dans un type de classe, la classe doit avoir un constructeur principal. Paramètres du constructeur doivent apparaître après le nom de type dans la définition de classe. A `let` liaison dans un type de classe définit les champs privés et les membres de ce type de classe et, avec `do` liaisons dans le type, le code du constructeur principal pour le type de formulaires. Les exemples de code suivants montrent une classe `MyClass` avec les champs privés `field1` et `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Les étendues de `field1` et `field2` sont limitées au type dans lequel ils sont déclarés. Pour plus d’informations, consultez [ `let` liaisons dans les Classes](../members/let-bindings-in-classes.md) et [Classes](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Paramètres de type dans les liaisons let

A `let` liaison au niveau du module dans un type, ou dans une expression de calcul peut avoir des paramètres de type explicite. Une liaison let dans une expression, comme dans une définition de fonction, ne peut pas avoir de paramètres de type. Pour plus d’informations, consultez [Génériques](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Attributs sur les liaisons let

Les attributs peuvent être appliqués au niveau supérieur `let` liaisons dans un module, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a>Portée et l’accessibilité des liaisons Let

L’étendue d’une entité déclarée avec une liaison let est limitée à la partie de l’objet contenant l’étendue (par exemple, une fonction, un module, fichier ou classe) une fois que la liaison s’affiche. Par conséquent, il peut être désignée qu’une liaison let introduit un nom dans une étendue. Dans un module, une valeur de liées à let ou une fonction est accessible aux clients d’un module tant que le module est accessible, étant donné que les liaisons let dans un module sont compilés dans des fonctions publiques du module. En revanche, les liaisons let dans une classe sont privées à la classe.

En règle générale, les fonctions dans les modules doivent être qualifiées par le nom du module lorsqu’il est utilisé par le code client. Par exemple, si un module `Module1` a une fonction `function1`, spécifient les utilisateurs `Module1.function1` pour faire référence à la fonction.

Les utilisateurs d’un module peuvent utiliser une déclaration d’importation à disposition les fonctions dans ce module pour une utilisation sans être qualifié par le nom du module. Dans l’exemple mentionnés ci-dessus, les utilisateurs du module peuvent ouvrir dans ce cas le module à l’aide de l’ouvrir de déclaration d’importation `Module1` et par la suite faire `function1` directement.

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Certains modules ont l’attribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), ce qui signifie que les fonctions qu’ils exposent doivent être qualifiées avec le nom du module. Par exemple, le module F # liste a cet attribut.

Pour plus d’informations sur les modules et contrôle d’accès, consultez [Modules](../modules.md) et [le contrôle d’accès](../access-control.md).

## <a name="see-also"></a>Voir aussi

[Fonctions](index.md)

[Liaisons `let` dans des classes](../members/let-bindings-in-classes.md)
