---
title: Tuples (F#)
description: "Découvrez le tuple F #, un regroupement de valeurs sans nom, mais ordonnées, de types éventuellement différents."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: c6a0565ac7022928f5c2bdad5387d896c6c3d387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tuples"></a>Tuples

A *tuple* est un regroupement de valeurs sans nom, mais ordonnées, de types éventuellement différents.  Tuples peut s’agir de types référence ou des structures.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>Remarques
Chaque *élément* dans la syntaxe précédente peut être toute expression valide de F #.

## <a name="examples"></a>Exemples
Les exemples de tuples de paires, triples et ainsi de suite, des types identiques ou différents. Certains exemples sont illustrés dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>Obtention de valeurs individuelles
Vous pouvez utiliser critères spéciaux pour accéder et affecter des noms pour les éléments de tuple, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Vous pouvez décomposer également un tuple via la recherche de correspondance en dehors d’un `match` expression via `let` liaison :

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Ou vous pouvez répéter correspondent dans les tuples comme entrées des fonctions :

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Si vous avez besoin qu’un seul élément de tuple, le caractère générique (trait de soulignement) peut être utilisé pour éviter de créer un nouveau nom pour une valeur que vous n’avez pas besoin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Copier des éléments à partir d’un tuple de référence dans un tuple d’un struct est également simple :

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Les fonctions `fst` et `snd` (référencer uniquement les tuples) retourne la première et deuxième élément d’un tuple, respectivement.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Il n’existe aucune fonction intégrée qui renvoie le troisième élément d’un triple, mais vous pouvez facilement écrire une comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

En général, il est préférable d’utiliser des critères spéciaux pour accéder à des éléments individuels d’un tuple.

## <a name="using-tuples"></a>À l’aide de Tuples
Tuples fournissent un moyen pratique de retourner plusieurs valeurs à partir d’une fonction, comme indiqué dans l’exemple suivant. Cet exemple effectue une division d’entier et retourne le résultat arrondi de l’opération en tant que premier membre d’une paire de tuple et le reste comme deuxième membre de la paire.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Tuples peuvent également servir en tant qu’arguments de fonction lorsque vous souhaitez éviter la curryfication implicite des arguments de fonction qui est impliquée par la syntaxe de fonction standard.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

La syntaxe habituelle pour la définition de la fonction `let sum a b = a + b` vous permet de définir une fonction qui est l’application partielle du premier argument de la fonction, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

À l’aide d’un tuple comme paramètre désactive la curryfication. Pour plus d’informations, consultez « Application partielle d’Arguments » dans [fonctions](functions/index.md).

## <a name="names-of-tuple-types"></a>Noms des Types de Tuple
Lorsque vous écrivez le nom d’un type qui est un tuple, vous utilisez la `*` symbole pour séparer les éléments. Pour un tuple qui se compose d’un `int`, un `float`et un `string`, tel que `(10, 10.0, "ten")`, le type est écrit comme suit.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Interopérabilité avec des Tuples c#

C# 7 introduit des tuples de la langue.  Tuples dans c# et sont des structures et sont équivalents aux tuples struct en F #.  Si vous avez besoin d’interagir avec c# utilise des tuples, vous devez utiliser des tuples de struct.

Il est facile à suivre.  Par exemple, imaginez que vous devez passer un tuple à une classe c# et ensuite utiliser son résultat, qui est également un tuple :

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

Dans votre code F #, vous pouvez passer un tuple d’un struct comme paramètre et consommer le résultat sous forme de tuple struct.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Conversion entre des Tuples de référence et les Tuples de Struct

Référence Tuples et Struct Tuples ayant une représentation sous-jacente complètement différente, ils ne sont pas implicitement convertibles.  Autrement dit, ne compilez les code semblable au suivant :

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Vous devez répéter correspondent dans un tuple et construire l’autre avec les parties qui le composent.  Exemple :

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Forme compilée de Tuples de référence
Cette section explique le formulaire de tuples quand elles sont compilées.  Les informations ici n’est pas nécessaire de lire, sauf si vous ciblez .NET Framework 3.5 ou inférieur.

Tuples sont compilés en objets de l’un des divers types génériques, tous appelés `System.Tuple`, qui sont surchargés sur l’arité, nombre de paramètres de type. Types de tuple apparaissent dans cet écran lorsque vous les affichez à partir d’un autre langage, tel que c# ou Visual Basic, ou lorsque vous utilisez un outil qui n’est pas conscient des constructions F #. Le `Tuple` types ont été introduits dans .NET Framework 4. Si vous ciblez une version antérieure du .NET Framework, le compilateur utilise les versions de [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) à partir de la version 2.0 de la bibliothèque principale F #. Les types dans cette bibliothèque sont utilisés uniquement pour les applications qui ciblent la version 2.0, 3.0 et les versions du .NET Framework 3.5. Transfert de type est utilisé pour assurer la compatibilité binaire entre les composants .NET Framework 2.0 et .NET Framework 4) (F #.

### <a name="compiled-form-of-struct-tuples"></a>Forme compilée de Tuples d’un Struct

Struct tuples (par exemple, `struct (x, y)`), sont fondamentalement différents à partir des tuples de référence.  Ils sont compilés dans le <xref:System.ValueTuple> type, surchargé par une arité, ou le nombre de paramètres de type.  Ils sont équivalents aux [C# 7 Tuples](../../csharp/tuples.md) et [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md)et interagir de façon bidirectionnelle.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Types F#](fsharp-types.md)
