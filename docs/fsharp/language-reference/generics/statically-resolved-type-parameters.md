---
title: "Paramètres de type résolus statiquement (F#)"
description: "Découvrez comment utiliser F # paramètre de type résolus statiquement, qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 14c629d6223584113af47636495be61decca02ad
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="statically-resolved-type-parameters"></a>Paramètres de type résolus statiquement

A *paramètre de type résolus statiquement* est un paramètre de type qui est remplacé par un type réel au moment de la compilation plutôt qu’au moment de l’exécution. Elles sont précédées par un signe insertion (^).


## <a name="syntax"></a>Syntaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Notes
Dans le langage F #, il existe deux types distincts de paramètres de type. Le premier type est le paramètre de type générique standard. Elles sont indiquées par une apostrophe ('), comme dans `'T` et `'U`. Ils sont équivalents aux paramètres de type générique dans d’autres langages .NET Framework. L’autre type est résolu statiquement et est indiqué par un symbole de point d’insertion, comme dans `^T` et `^U`.

Paramètres de type résolus statiquement sont essentiellement utiles conjointement aux contraintes de membre, qui sont des contraintes qui vous permettent de spécifier qu’un argument de type doit avoir un membre particulier ou les membres pour pouvoir être utilisé. Il n’existe aucun moyen pour créer ce type de contrainte à l’aide d’un paramètre de type générique normal.

Le tableau suivant récapitule les similitudes et les différences entre les deux types de paramètres de type.

|Fonctionnalité|Générique|Résolus statiquement|
|-------|-------|-------------------|
|Syntaxe|`'T`, `'U`|`^T`, `^U`|
|Temps de résolution|Au moment de l'exécution|Moment de la compilation|
|Contraintes de membre|Ne peut pas être utilisé avec les contraintes de membre.|Peut être utilisé avec les contraintes de membre.|
|Génération de code|Un type (ou une méthode) avec des paramètres de type générique standard entraîne la génération d’un type générique unique ou une méthode.|Plusieurs instanciations de types et méthodes sont générées, un pour chaque type qui est nécessaire.|
|Utiliser avec des types|Peut être utilisé sur les types.|Ne peut pas être utilisé sur les types.|
|Utiliser avec les fonctions inline|Non. Une fonction inline ne peut pas être paramétrée avec un paramètre de type générique standard.|Oui. Paramètres de type résolus statiquement ne peut pas être utilisés sur les fonctions ou méthodes qui ne sont pas inline.|

Nombreuses fonctions F # core library, notamment les opérateurs, ont des paramètres de type résolus statiquement. Ces fonctions et opérateurs sont inline et entraînent la génération de code efficace pour les calculs numériques.

Méthodes inline et les fonctions qui utilisent des opérateurs, ou utilisent d’autres fonctions qui ont des paramètres de type résolus statiquement peuvent également utiliser des paramètres de type résolus statiquement proprement dits. Souvent, l’inférence de type déduit ces fonctions inline ont des paramètres de type résolus statiquement. L’exemple suivant illustre une définition d’opérateur est déduite comme ayant un paramètre de type résolus statiquement.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

Le type résolu de `(+@)` est basée sur l’utilisation des deux `(+)` et `(*)`, à la fois qui amènent l’inférence de type déduire les contraintes de membre sur les paramètres de type résolus statiquement. Le type résolu, comme indiqué dans l’interpréteur F #, est comme suit.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

La sortie est la suivante.

```
2
1.500000
```

À compter de F # 4.1, vous pouvez également spécifier les noms de type concret dans les signatures de paramètres de type résolus statiquement.  Dans les versions précédentes de la langue, le nom de type peut effectivement être déduit par le compilateur, mais n’a pas réellement être spécifié dans la signature.  À compter de F # 4.1, vous pouvez également spécifier des noms de type concret dans les signatures de paramètres de type résolus statiquement. Voici un exemple :

```fsharp
type CFunctor() = 
      static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
      static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

      // default implementation of replace
      static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

      // call overridden replace if present
      static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
      ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Voir aussi
[Génériques](index.md)

[Inférence de type](../type-inference.md)

[Généralisation automatique](automatic-generalization.md)

[Contraintes](constraints.md)

[Fonctions inline](../functions/inline-functions.md)
