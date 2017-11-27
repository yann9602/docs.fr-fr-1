---
title: Liaisons let dans les classes (F#)
description: "Apprendre à définir des champs privés et des fonctions privées pour des classes F # à l’aide de liaisons 'let' dans la définition de classe."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a>Liaisons let dans des classes

Vous pouvez définir des champs privés et des fonctions privées pour les classes F # à l’aide de `let` liaisons dans la définition de classe.


## <a name="syntax"></a>Syntaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Remarques
La syntaxe précédente apparaît après les déclarations de titre et l’héritage de classe, mais avant les définitions de membre. La syntaxe est similaire à celle de `let` liaisons en dehors des classes, mais les noms définis dans une classe ont une portée limitée à la classe. A `let` liaison crée un champ privé ou une fonction ; pour exposer des données ou les fonctions déclarer publiquement, une propriété ou une méthode membre.

A `let` de liaison qui n’est pas statique est appelée une instance `let` liaison. Instance `let` liaisons s’exécutent lorsque des objets sont créés. Statique `let` liaisons font partie de l’initialiseur statique pour la classe, qui est garantie à exécuter avant le type est utilisé pour la première fois.

Le code au sein de l’instance `let` liaisons puissent utiliser les paramètres du constructeur principal.

Attributs et les modificateurs d’accessibilité ne sont pas autorisés sur `let` liaisons dans les classes.

Les exemples de code suivants illustrent plusieurs types de `let` liaisons dans les classes.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

La sortie est la suivante.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Autres manières de créer des champs
Vous pouvez également utiliser le `val` (mot clé) pour créer un champ privé. Lorsque vous utilisez la `val` (mot clé), le champ pas une valeur est attribué lors de l’objet est créé, mais est initialisé avec une valeur par défaut. Pour plus d’informations, consultez [champs explicites : val (mot clé)](explicit-fields-the-val-keyword.md).

Vous pouvez également définir des champs privés dans une classe en utilisant une définition de membre et en ajoutant le mot clé `private` à la définition. Cela peut être utile si vous envisagez de modifier l’accessibilité d’un membre sans réécrire votre code. Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).

## <a name="see-also"></a>Voir aussi
[Membres](index.md)

[Liaisons `do` dans des classes](do-bindings-in-classes.md)

[`let`Liaisons](../functions/let-bindings.md)
