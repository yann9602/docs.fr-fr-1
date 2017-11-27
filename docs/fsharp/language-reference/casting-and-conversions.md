---
title: Cast et conversions (F#)
description: "Découvrez comment le langage de programmation F # fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: f17d3919c59c5881213d28a59cea7ae184493949
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="casting-and-conversions-f"></a>Cast et conversions (F#)

Cette rubrique décrit la prise en charge des conversions de type en F #.

## <a name="arithmetic-types"></a>Types arithmétiques
F # fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs, tels qu’entre entier et les types à virgule flottante. Les opérateurs de conversion de type intégral et de caractère ont vérifié et les formulaires est désactivées ; opérateurs à virgule flottante et `enum` opérateur de conversion ne sont pas. Les écrans désactivées sont définies dans `Microsoft.FSharp.Core.Operators` et les formes vérifiées sont définies dans `Microsoft.FSharp.Core.Operators.Checked`. Les formes vérifiées vérification de dépassement de capacité et génèrent une exception runtime si la valeur obtenue dépasse les limites du type cible.

Chacun de ces opérateurs a le même nom que le nom du type de destination. Par exemple, dans le code suivant, dans lequel les types sont annotés explicitement, `byte` apparaît avec deux significations différentes. La première occurrence est le type et le deuxième est l’opérateur de conversion.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

Le tableau suivant présente les opérateurs de conversion définis en F #.

|Opérateur|Description|
|--------|-----------|
|`byte`|Convertir en octet, un type non signé 8 bits.|
|`sbyte`|Convertir en octet signé.|
|`int16`|Convertir en un entier signé 16 bits.|
|`uint16`|Convertir un entier non signé 16 bits.|
|`int32, int`|Convertir en un entier signé 32 bits.|
|`uint32`|Convertir un entier non signé 32 bits.|
|`int64`|Convertir en un entier signé 64 bits.|
|`uint64`|Convertir un entier non signé 64 bits.|
|`nativeint`|Convertir un entier natif.|
|`unativeint`|Convertir un entier natif non signé.|
|`float, double`|Convertir à double précision IEEE 64 bits nombre à virgule flottante.|
|`float32, single`|Convertir à simple précision IEEE 32 bits nombre à virgule flottante.|
|`decimal`|Convertir en `System.Decimal`.|
|`char`|Convertir en `System.Char`, un caractère Unicode.|
|`enum`|Convertir en un type énuméré.|
En plus des types primitifs intégrés, vous pouvez utiliser ces opérateurs avec les types qui implémentent `op_Explicit` ou `op_Implicit` méthodes avec les signatures appropriées. Par exemple, le `int` opérateur de conversion fonctionne avec tout type qui fournit une méthode statique `op_Explicit` qui prend le type en tant que paramètre et retourne `int`. Constitue une exception à la règle générale est que les méthodes ne peuvent pas être surchargées par type de retour, vous pouvez faire à `op_Explicit` et `op_Implicit`.

## <a name="enumerated-types"></a>Types énumérés
Le `enum` opérateur est un opérateur générique qui prend un paramètre de type qui représente le type de le `enum` à convertir. Tente de déterminer le type de l’inférence de type lorsqu’il convertit un type énuméré, le `enum` que vous souhaitez convertir. Dans l’exemple suivant, la variable `col1` n’est pas annotée explicitement, mais son type est déduit du test d’égalité ultérieur. Par conséquent, le compilateur peut déduire que vous convertissez un `Color` énumération. Vous pouvez également fournir une annotation de type, comme avec `col2` dans l’exemple suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
Vous pouvez également spécifier le type d’énumération cible explicitement comme paramètre de type, comme dans le code suivant :

```fsharp
let col3 = enum<Color> 3
```

Notez que l’énumération convertit de travail uniquement si le type sous-jacent de l’énumération est compatible avec le type en cours de conversion. Dans le code suivant, la conversion ne parvient pas à compiler en raison de l’incompatibilité entre `int32` et `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Pour plus d’informations, consultez [énumérations](enumerations.md).

## <a name="casting-object-types"></a>Conversion des Types d’objets
Conversion entre types dans une hiérarchie d’objets est essentielle à la programmation orientée objet. Il existe deux types de conversions : cast ascendant (cast ascendant) et de la conversion vers le bas (cast). Conversion d’une hiérarchie signifie effectuer un cast à partir d’une référence d’objet dérivé vers une référence d’objet de base. Ce type de conversion garantit un fonctionnement correct, que la classe de base est dans la hiérarchie d’héritage de la classe dérivée. Effectuer un cast vers le bas d’une hiérarchie, à partir d’une référence d’objet de base pour une référence d’objet dérivé, ne réussit que si l’objet est en fait une instance du type (dérivé) de destination correct ou un type dérivé du type de destination.

F # fournit des opérateurs pour ces types de conversions. Le `:>` effectue un cast de l’opérateur dans la hiérarchie et le `:?>` opérateur effectue un cast vers le bas de la hiérarchie.

### <a name="upcasting"></a>Cast ascendant
Dans de nombreux langages orientés objet, le cast ascendant est implicite ; en F #, les règles sont légèrement différentes. Cast ascendant est appliqué automatiquement lorsque vous passez des arguments aux méthodes du type d’objet. Toutefois, pour les fonctions liées à let dans un module, cast ascendant n’est pas automatique, sauf si le type de paramètre est déclaré comme un type flexible. Pour plus d’informations, consultez [Types flexibles](flexible-Types.md).

Le `:>` opérateur effectue un cast statique, ce qui signifie que la réussite du cast est déterminée au moment de la compilation. Si un cast qui utilise `:>` se compile correctement, il cast est valide et n’a aucun risque d’échouer au moment de l’exécution.

Vous pouvez également utiliser le `upcast` opérateur pour effectuer une telle conversion. L’expression suivante spécifie une conversion de la hiérarchie :

```fsharp
upcast expression
```

Lorsque vous utilisez l’opérateur upcast, le compilateur tente de déduire le type que vous convertissez à partir du contexte. Si le compilateur est incapable de déterminer le type de cible, le compilateur signale une erreur.

### <a name="downcasting"></a>Cast descendant
Le `:?>` opérateur effectue un cast dynamique, ce qui signifie que la réussite du cast est déterminée au moment de l’exécution. Un cast qui utilise le `:?>` opérateur n’est pas vérifiée au moment de la compilation, mais au moment de l’exécution, une tentative est effectuée pour effectuer un cast vers le type spécifié. Si l’objet est compatible avec le type de cible, le cast réussit. Si l’objet n’est pas compatible avec le type de cible, le runtime déclenche un `InvalidCastException`.

Vous pouvez également utiliser le `downcast` opérateur pour effectuer une conversion de type dynamique. L’expression suivante spécifie une conversion vers le bas de la hiérarchie à un type qui est déduit à partir du contexte de programme :

```fsharp
downcast expression
```

Comme pour les `upcast` (opérateur), si le compilateur ne peut pas déduire un type de cible spécifique à partir du contexte, il signale une erreur.

Le code suivant illustre l’utilisation de la `:>` et `:?>` opérateurs. Le code illustre les `:?>` opérateur convient lorsque vous savez que la conversion réussira, car il lève `InvalidCastException` si la conversion échoue. Si vous ne connaissez pas qu’une conversion réussit, un test de type qui utilise un `match` expression est préférable car elle évite la surcharge de la génération d’une exception.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Étant donné que les opérateurs génériques `downcast` et `upcast` s’appuient sur l’inférence de type pour déterminer le type d’arguments et de retour dans le code ci-dessus, vous pouvez remplacer

```fsharp
let base1 = d1 :> Base1
```

par

```fsharp
base1 = upcast d1
```

Dans le code précédent, le type d’argument et les types de retour sont `Derived1` et `Base1`, respectivement.

Pour plus d’informations sur les tests de type, consultez [Expressions de correspondance](match-Expressions.md).

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
