---
title: Enregistrements (F#)
description: "Découvrez comment F # enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a>Enregistrements

Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.  Depuis 4.1 F #, ils peuvent être soit structs ou référence des types.  Ils sont des types de référence par défaut.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>Notes
Dans la syntaxe précédente, *typename* est le nom du type d’enregistrement, *label1* et *label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs. *liste des membres* est la liste facultative de membres pour le type.  Vous pouvez utiliser la `[<Struct>]` attribut pour créer un enregistrement de struct plutôt qu’un enregistrement qui est un type référence.

Voici quelques exemples.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.

Vous pouvez définir des valeurs dans les expressions appelées *enregistrer expressions*. Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment distinctes de celles des autres types d’enregistrements). L’expression d’enregistrement placez-le entre accolades ({}). Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec étiquettes `x`, `y` et `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

S’il peut y avoir un autre type qui possède également les étiquettes de mêmes, n’utilisez pas la forme abrégée.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Les étiquettes du type plus récemment déclaré ont priorité sur ceux du type déclaré précédemment, c’est le cas dans l’exemple précédent, `mypoint3D` est déduit que `Point3D`. Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Méthodes peuvent être définies pour les types d’enregistrements, comme pour des types de classe.

## <a name="creating-records-by-using-record-expressions"></a>Création d’enregistrements à l’aide d’Expressions d’enregistrement
Vous pouvez initialiser des enregistrements en utilisant les étiquettes qui sont définis dans l’enregistrement. Une expression qui effectue l’opération est appelée un *enregistrer expression*. Utiliser des accolades pour encadrer l’expression d’enregistrement et le point-virgule comme délimiteur.

L’exemple suivant montre comment créer un enregistrement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

Les points-virgules après le dernier champ dans l’expression d’enregistrement et la définition de type sont facultatifs, que les champs soient tous sur une ligne.

Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ. Vous ne pouvez pas référencer les valeurs des autres champs dans l’expression d’initialisation d’un champ.

Dans le code suivant, le type de `myRecord2` est déduit des noms des champs. Si vous le souhaitez, vous pouvez spécifier le nom de type explicitement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines des valeurs du champ. La ligne de code suivante illustre ce comportement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Cette forme de l’expression d’enregistrement est appelée le *copier et mettre à jour des enregistrement expression*.

Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez facilement créer des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour. Vous pouvez également spécifier explicitement un champ mutable.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

N’utilisez pas l’attribut DefaultValue avec les champs d’enregistrement. Une meilleure approche consiste à définir des instances par défaut des enregistrements avec des champs qui sont initialisés les valeurs par défaut puis utiliser une copie et mise à jour d’expression d’enregistrement pour définir les champs qui diffèrent des valeurs par défaut.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Mise en correspondance avec des enregistrements
Enregistrements peuvent être utilisés avec les critères spéciaux. Vous pouvez spécifier des champs explicitement et fournir des variables pour les autres champs qui seront attribués lorsqu’une correspondance se produit. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

La sortie de ce code est comme suit.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Différences entre les Classes et les enregistrements
Champs d’enregistrement diffèrent des classes dans la mesure où ils sont automatiquement exposés en tant que propriétés, et ils sont utilisés lors de la création et de copie d’enregistrements. La construction d’enregistrement diffère également de construction de la classe. Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur. Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique. Classes ont aucune relation directe entre les paramètres du constructeur, des champs et propriétés.

Comme les types d’union et de structure, les enregistrements ont une sémantique d’égalité structurelle. Classes ont référence une sémantique d’égalité. L’exemple de code suivant illustre cela.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Si vous écrivez le même code avec les classes, les deux objets de classe seraient inégaux parce que les deux valeurs représenteraient deux objets sur le tas et seules les adresses seraient comparées (à moins que le type de classe substitue le `System.Object.Equals` méthode).

Si vous avez besoin de l’égalité pour les enregistrements de référence, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.

## <a name="see-also"></a>Voir aussi
[Types F#](fsharp-types.md)

[Classes](classes.md)

[Informations de référence du langage F#](index.md)

[Égalité des références](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[Critères spéciaux](pattern-matching.md)
