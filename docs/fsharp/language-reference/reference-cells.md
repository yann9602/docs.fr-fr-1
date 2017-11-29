---
title: "Cellules de référence (F#)"
description: "Découvrez comment les cellules de référence de F # sont les emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a>Cellules de référence

*Cellules de référence* sont des emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence.

## <a name="syntax"></a>Syntaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Remarques
Pour créer une cellule de référence qui encapsule la valeur, utilisez l'opérateur `ref`. Vous pouvez ensuite modifier la valeur sous-jacente, car elle est mutable.

Une cellule de référence contient une valeur réelle, et pas uniquement une adresse. Lorsque vous créez une cellule de référence à l'aide de l'opérateur `ref`, vous créez une copie de la valeur sous-jacente en tant que valeur mutable encapsulée.

Vous pouvez déréférencer une cellule de référence à l'aide de l'opérateur `!` (bang).

L'exemple de code suivant illustre la déclaration et l'utilisation de cellules de référence.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Le résultat est `50`.

Les cellules de référence sont des instances du type d'enregistrement générique `Ref` qui est déclaré comme suit.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Le type `'a ref` (affiché par le compilateur et IntelliSense dans l'IDE) est un synonyme de `Ref<'a>` (définition sous-jacente).

L'opérateur `ref` crée une cellule de référence. Le code suivant est la déclaration de l'opérateur `ref`.

```fsharp
let ref x = { contents = x }
```

Le tableau suivant répertorie les fonctionnalités disponibles sur la cellule de référence.

|Opérateur, membre ou champ|Description|Type|Définition|
|--------------------------|-----------|----|----------|
|`!` (opérateur de déréférence)|Retourne la valeur sous-jacente.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (opérateur d'assignation)|Modifie la valeur sous-jacente.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (opérateur)|Encapsule une valeur dans une nouvelle cellule de référence.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (propriété)|Obtient ou définit la valeur sous-jacente.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (champ d'enregistrement)|Obtient ou définit la valeur sous-jacente.|`'a`|`let ref x = { contents = x }`|
Vous pouvez accéder à la valeur sous-jacente de plusieurs façons. La valeur retournée par l'opérateur de déréférence (`!`) n'est pas une valeur assignable. Par conséquent, si vous modifiez la valeur sous-jacente, vous devez utiliser à la place l'opérateur d'assignation (`:=`).

La propriété `Value` et le champ `contents` sont des valeurs assignables. Par conséquent, vous pouvez les utiliser pour accéder ou modifier la valeur sous-jacente, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

La sortie est la suivante.

```
10
10
11
12
```

Le champ `contents` est fourni à des fins de compatibilité avec d'autres versions de ML et produit un avertissement au cours de la compilation. Pour désactiver l'avertissement, utilisez l'option de compilateur `--mlcompatibility`. Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).

Le code suivant illustre l'utilisation de cellules de référence dans le cadre du passage de paramètres. Le type de l’incrémentation du a une méthode incrément qui prend un paramètre qui inclut le type de paramètre byref. Dans le type de paramètre byref indique que les appelants doivent passer une cellule de référence ou l’adresse d’une variable normale du type spécifié, dans ce cas int : Le code restant illustre comment appeler un incrément avec ces deux types d’arguments et illustre l’utilisation de l’opérateur ref sur une variable pour créer une cellule de référence (ref myDelta1). Il montre ensuite l'utilisation de l'opérateur d'adresse (&amp;) pour générer un argument approprié. Enfin, la méthode de l’incrément est appelée à nouveau à l’aide d’une cellule de référence déclarée à l’aide d’une liaison let. La dernière ligne de code illustre l’utilisation de la ! opérateur pour déréférencer la cellule de référence pour l’impression.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Pour plus d’informations sur le passage par référence, consultez [paramètres et Arguments](parameters-and-arguments.md).

>[!NOTE]
Les programmeurs c# doivent savoir que ref différemment en F # fonctionne et en c#. Par exemple, l’utilisation de ref lorsque vous passez un argument n’a pas le même effet en F # et en c#.

## <a name="consuming-c-ref-returns"></a>Utilisation de c# `ref` retourne

À compter de F # 4.1, vous pouvez utiliser `ref` retourne généré en c#.  Le résultat de cet appel est un `byref<_>` pointeur.

La méthode c# suivante :

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

Peut être appelée en toute transparence par F # avec aucune syntaxe particulière :

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Vous pouvez également déclarer des fonctions, ce qui peut prendre un `ref` retourner en tant qu’entrée, par exemple :

```fsharp
let f (x: byref<int>) = &x
```

Il n’existe actuellement aucun moyen de générer un `ref` retour en F #, qui peut être consommé en c#.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Paramètres et arguments](parameters-and-arguments.md)

[Informations de référence des symboles et opérateurs](symbol-and-operator-reference/index.md)
