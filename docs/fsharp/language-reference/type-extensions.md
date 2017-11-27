---
title: Extensions de type (F#)
description: "Découvrez comment les extensions de type F # permettent de que vous ajoutez de nouveaux membres à un type d’objet précédemment défini."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a>Extensions de type

Extensions de type vous permettent d’ajouter de nouveaux membres à un type d’objet précédemment défini.

## <a name="syntax"></a>Syntaxe

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>Remarques
Il existe deux formes d’extensions de type qui ont des comportements et une syntaxe légèrement différente. Un *extension intrinsèque* est une extension qui s’affiche dans le même espace de noms ou module, dans le même fichier source et dans le même assembly (DLL ou fichier exécutable) que le type étendu. Un *extension facultative* est une extension qui apparaît en dehors du module, espace de noms ou assembly du type en cours d’extension d’origine. Les extensions intrinsèques apparaissent sur le type lorsque le type est examiné par réflexion, mais pas des extensions facultatives. Facultatif pour les extensions doivent être dans des modules et sont uniquement dans la portée lorsque le module qui contient l’extension est ouvert.

Dans la syntaxe précédente, *typename* représente le type qui est étendu. N’importe quel type accessible peut être étendu, mais le nom de type doit être un nom de type réel, pas une abréviation de type. Vous pouvez définir plusieurs membres dans une extension de type. Le *auto-identificateur* représente l’instance de l’objet qui est appelée, comme dans des membres ordinaires.

Le `end` mot clé est facultatif dans la syntaxe simplifiée.

Les membres définis dans les extensions de type peuvent être utilisés comme les autres membres sur un type de classe. Comme d’autres membres, ils peuvent être statiques ou membres d’instance. Ces méthodes sont également appelés *les méthodes d’extension*; propriétés sont appelées *propriétés d’extension*, et ainsi de suite. Membres d’extension facultatifs sont compilés en membres statiques pour lequel l’instance d’objet est passée implicitement comme premier paramètre. Toutefois, ils agissent comme si elles étaient des membres d’instance ou des membres statiques en fonction de la façon dont ils sont déclarés. Membres d’extension implicites sont inclus en tant que membres du type et peuvent être utilisés sans restriction.

Méthodes d’extension ne peut pas être des méthodes virtuelles ou abstraites. Elles peuvent surcharger d’autres méthodes portant le même nom, mais le compilateur donne la préférence des méthodes d’extension non dans le cas d’un appel ambigu.

Si plusieurs extensions de type intrinsèque existent pour un type, tous les membres doivent être uniques. Pour les extensions de type facultatif, les membres dans différentes extensions de type vers le même type peuvent avoir le même nom. Erreurs d’ambiguïté se produisent uniquement si le code client ouvre deux portées différentes qui définissent les mêmes noms de membre.

Dans l’exemple suivant, un type dans un module a une extension de type intrinsèque. Au code client en dehors du module, l’extension de type apparaît comme un membre standard du type à tous les égards.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

Vous pouvez utiliser des extensions de type intrinsèque pour séparer la définition d’un type en sections. Cela peut être utile pour gérer les définitions de type de grande taille, par exemple, pour séparer le code généré par le compilateur et le code créé ou permettent de regrouper de code créés par différentes personnes ou associés à des fonctionnalités différentes.

Dans l’exemple suivant, une extension de type facultative étend la `System.Int32` type avec une méthode d’extension `FromString` qui appelle le membre statique `Parse`. Le `testFromString` méthode montre que le nouveau membre est appelé comme n’importe quel membre d’instance.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

Le nouveau membre d’instance apparaît comme toute autre méthode de la `Int32` type dans IntelliSense, mais uniquement lorsque le module qui contient l’extension est ouvert ou dans la portée.

## <a name="generic-extension-methods"></a>Méthodes d’Extension générique
Avant de F # 3.1, le compilateur F # n’a pas prendre en charge l’utilisation du langage c#-style de méthodes d’extension avec une variable de type générique, type de tableau, type de tuple ou un type de fonction F # comme paramètre de « THI ». F # 3.1 prend en charge l’utilisation de ces membres d’extension.

Par exemple, dans le code F # 3.1, vous pouvez utiliser les méthodes d’extension avec des signatures qui ressemblent à la syntaxe suivante en c# :

```csharp
static member Method<T>(this T input, T other)
```

Cette approche est particulièrement utile lorsque le paramètre de type générique est limité. En outre, vous pouvez désormais déclarer les membres d’extension comme suit dans le code F # et définir un ensemble supplémentaire, sémantiquement riche de méthodes d’extension. En F #, vous définissez généralement les membres d’extension comme le montre l’exemple suivant :

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

Toutefois, pour un type générique, la variable de type ne peut pas être contraints. Vous pouvez désormais déclarer c#-membre d’extension de style en F # pour contourner cette limitation. Lorsque vous combinez ce type de déclaration avec la fonctionnalité inline de F #, vous pouvez présenter les algorithmes génériques en tant que membres d’extension.

Prenons la déclaration suivante :

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

À l’aide de cette déclaration, vous pouvez écrire du code qui ressemble à l’exemple suivant.

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

Dans ce code, le même code arithmétique générique est appliqué aux listes de deux types sans surcharge, en définissant un membre de la même extension.


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Membres](members/index.md)
