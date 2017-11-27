---
title: Espaces de noms (F#)
description: "Découvrez comment un espace de noms F # permet d’organiser le code dans des zones de fonctionnalités connexes en vous permettant de joindre un nom à un regroupement d’éléments de programme."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: 4378afebe6fd0d9317f734457576dc75d7488bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces"></a>Espaces de noms

Un espace de noms vous permet d’organiser le code en zones de fonctionnalités connexes. Pour cela, vous attachez un nom à un regroupement d’éléments de programme.


## <a name="syntax"></a>Syntaxe

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Remarques
Si vous souhaitez placer le code dans un espace de noms, la première déclaration dans le fichier doit déclarer l’espace de noms. Le contenu du fichier entier fait alors partie de l’espace de noms.

Espaces de noms ne peut pas contenir directement de valeurs et des fonctions. Au lieu de cela, les fonctions et les valeurs doivent être incluses dans les modules et les modules sont inclus dans les espaces de noms. Espaces de noms peuvent contenir des types, des modules.

Espaces de noms peuvent être déclarés explicitement avec le mot clé d’espace de noms, ou implicitement lors de la déclaration d’un module. Pour déclarer un espace de noms explicitement, utilisez le mot clé namespace suivi du nom de l’espace de noms. L’exemple suivant montre un fichier de code qui déclare un espace de noms Widgets avec un type et un module inclus dans cet espace de noms.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Si le contenu entier du fichier est dans un module, vous pouvez également déclarer espaces de noms implicitement à l’aide de la `module` (mot clé) et en fournissant le nouveau nom d’espace de noms dans le nom du module complet. L’exemple suivant montre un fichier de code qui déclare un espace de noms `Widgets` et un module `WidgetsModule`, qui contient une fonction.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Le code suivant est équivalent au code précédent, mais le module est une déclaration de module locale. Dans ce cas, l’espace de noms doit apparaître sur sa propre ligne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Si plusieurs modules est requise dans le même fichier dans un ou plusieurs espaces de noms, vous devez utiliser des déclarations de module locales. Lorsque vous utilisez des déclarations de module locales, vous ne pouvez pas utiliser l’espace de noms qualifié dans les déclarations de module. Le code suivant montre un fichier qui a une déclaration d’espace de noms et deux déclarations de module locales. Dans ce cas, les modules sont contenus directement dans l’espace de noms ; Il n’existe aucun module créé implicitement qui porte le même nom que le fichier. N’importe quel autre code dans le fichier, tel qu’un `do` , la liaison est dans l’espace de noms mais pas dans les modules internes, vous devez qualifier le membre de module `widgetFunction` en utilisant le nom de module.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

La sortie de cet exemple est la suivante.

```fsharp
Module1 10 20
Module2 5 6
```

Pour plus d’informations, consultez [Modules](modules.md).

## <a name="nested-namespaces"></a>Espaces de noms imbriqués
Lorsque vous créez un espace de noms imbriqué, vous devez le qualifier complètement. Sinon, vous créez un nouvel espace de noms de niveau supérieur. Mise en retrait est ignorée dans les déclarations d’espace de noms.

L’exemple suivant montre comment déclarer un espace de noms imbriqué.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Espaces de noms de fichiers et des assemblys
Espaces de noms peut s’étendre sur plusieurs fichiers dans un projet unique ou de la compilation. Le terme *fragment de l’espace de noms* décrit la partie d’un espace de noms qui est inclus dans un fichier. Espaces de noms peut également couvrir plusieurs assemblys. Par exemple, le `System` espace de noms inclut l’ensemble .NET Framework, qui couvre de nombreux assemblys et qui contient plusieurs espaces de noms imbriqués.


## <a name="global-namespace"></a>Global Namespace
Vous utilisez l’espace de noms prédéfini `global` pour mettre des noms dans l’espace de noms de niveau supérieur .NET.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Vous pouvez également utiliser global pour référencer l’espace de noms .NET niveau supérieur, par exemple, pour résoudre des conflits de noms avec d’autres espaces de noms.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

##

F # 4.1 introduit la notion d’espaces de noms permettant à tous les contenus du code mutuellement récursive.  Cette opération est effectuée `namespace rec`.  Utilisation de `namespace rec` peut atténuer certains problèmes dans l’impossibilité d’écrire du code mutuellement référentielle entre les types et des modules.  Voici un exemple :

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

Notez que l’exception `DontSqueezeTheBananaException` et la classe `Banana` font référence à l’autre.  En outre, le module `BananaHelpers` et la classe `Banana` également faire référence à l’autre.  Cela ne serait pas possible d’exprimer dans F #, si vous avez supprimé le `rec` (mot clé) à partir de la `MutualReferences` espace de noms.

Cette fonctionnalité est également disponible pour niveau supérieur [Modules](modules.md) dans F # 4.1 ou version ultérieure.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Modules](modules.md)

[F # RFC FS-1009 - autoriser les modules et types mutuellement référentielles sur étendues supérieure dans les fichiers](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
