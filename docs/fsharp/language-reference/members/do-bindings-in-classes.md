---
title: Liaisons do dans les classes (F#)
description: "Découvrez comment utiliser une liaison dans une définition de classe, qui effectue des actions lorsque l’objet est construit ou le type de la première utilisation de ' do' F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a>Liaisons do dans les classes

A `do` liaison dans une définition de classe exécute des actions lorsque l’objet est construit ou, pour une analyse statique `do` de liaison, lorsque la première utilisation du type.


## <a name="syntax"></a>Syntaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Remarques
A `do` liaison apparaît avec ou après `let` liaisons mais avant les définitions de membre dans une définition de classe. Bien que le `do` (mot clé) est facultatif pour `do` liaisons au niveau du module, il n’est pas facultatif pour `do` liaisons dans une définition de classe.

Pour la construction de chaque objet d’un type donné, non statique `do` liaisons et non statiques `let` sont exécutées dans l’ordre dans lequel elles apparaissent dans la définition de classe. Plusieurs `do` liaisons peuvent se produire dans un type. Non statiques `let` liaisons et non statiques `do` liaisons devient le corps du constructeur principal. Le code non statiques `do` section des liaisons peut référencer les paramètres du constructeur principal et des valeurs ou des fonctions qui sont définies dans la `let` section des liaisons.

Non statiques `do` liaisons peuvent accéder aux membres de la classe tant que la classe a un auto-identificateur défini par un `as` mot clé dans la classe de titre et tant que toutes les utilisations de ces membres sont qualifiées avec l’auto-identificateur pour la classe.

Étant donné que `let` liaisons initialisent les champs privés d’une classe, qui est souvent nécessaire pour garantir que les membres se comportent comme prévu, `do` liaisons sont généralement placées après `let` liaisons afin que le code dans le `do` peut de liaison s’exécuter avec un objet entièrement initialisé. Si votre code tente d’utiliser un membre avant l’initialisation est terminée, une exception InvalidOperationException est déclenchée.

Statique `do` liaisons peuvent référencer des membres statiques ou champs de la classe, mais pas les membres ou les champs d’instance. Statique `do` liaisons font partie de l’initialiseur statique pour la classe, qui est garantie s’exécute avant la première utilisation de la classe.

Les attributs sont ignorés pour `do` liaisons dans les types. Si un attribut est requis pour le code qui s’exécute dans un `do` de liaison, il doit être appliqué à un constructeur principal.

Dans le code suivant, une classe a un statique `do` de liaison et non statiques `do` liaison. L’objet a un constructeur qui possède deux paramètres, `a` et `b`, et deux champs privés sont définis dans le `let` liaisons pour la classe. Deux propriétés sont également définies. Tous ces éléments sont dans la portée de la non statique `do` section des liaisons, comme cela est illustré par la ligne qui imprime toutes ces valeurs.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

La sortie est la suivante.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Voir aussi
[Membres](index.md)

[Classes](../classes.md)

[Constructeurs](constructors.md)

[Liaisons `let` dans des classes](let-bindings-in-classes.md)

[`do`Liaisons](../functions/do-Bindings.md)
