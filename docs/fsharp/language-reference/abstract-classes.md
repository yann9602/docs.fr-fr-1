---
title: Classes abstraites (F#)
description: "En savoir plus sur les classes abstraites F #, qui laissent certains ou tous les membres non implémentés et représentent des fonctionnalités communes de différents types de types d’objet."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a>Classes abstraites

*Classes abstraites* sont des classes qui laissent certains ou tous les membres non implémentés, afin que les implémentations puissent être fournies par les classes dérivées.

## <a name="syntax"></a>Syntaxe

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Remarques
Dans la programmation orientée objet, une classe abstraite est utilisée comme classe de base d’une hiérarchie et représente les fonctionnalités communes de différents types de types d’objet. Comme l’indique l’abstraite « nom », les classes abstraites ne correspondent pas souvent directement à des entités concrètes dans le domaine de problème. Toutefois, elles ne représentent que nombreuses entités concrètes ont en commun.

Classes abstraites doivent avoir le `AbstractClass` attribut. Ils peuvent ont implémenté et non implémenté des membres. L’utilisation du terme *abstraite* quand il est appliqué à une classe est la même que dans d’autres langages .NET ; Toutefois, l’utilisation du terme *abstraite* quand il est appliqué aux méthodes (et des propriétés) est un peu différente en F # à partir de son utiliser dans d’autres langages .NET. En F #, lorsqu’une méthode est marquée avec la `abstract` (mot clé), cela indique qu’un membre a une entrée, appelée un *emplacement de dispatch virtuel*, dans la table interne des fonctions virtuelles pour ce type. En d’autres termes, la méthode est virtuelle, bien que le `virtual` mot clé n’est pas utilisé dans le langage F #. Le mot clé `abstract` est utilisé pour les méthodes virtuelles, quelle que soit la méthode est implémentée ou non. La déclaration d’un emplacement de dispatch virtuel est séparée de la définition d’une méthode pour cet emplacement de dispatch. Par conséquent, l’équivalent en F # d’une déclaration de méthode virtuelle et la définition dans un autre langage .NET est une combinaison d’une déclaration de méthode abstraite et d’une définition séparée, avec l’option le `default` mot clé ou le `override` (mot clé). Pour plus d’informations et d’exemples, consultez [méthodes](members/methods.md).

Une classe est considérée comme abstraite uniquement s’il existe des méthodes abstraites qui sont déclarés mais pas définis. Par conséquent, les classes qui ont des méthodes abstraites ne sont pas nécessairement des classes abstraites. Si une classe a des méthodes abstraites non définies, n’utilisez pas le **AbstractClass** attribut.

Dans la syntaxe précédente, *modificateur d’accessibilité* peut être `public`, `private` ou `internal`. Pour plus d’informations, consultez [Contrôle d’accès](access-control.md).

Comme avec d’autres types, les classes abstraites peuvent avoir une classe de base et un ou plusieurs interfaces de base. Chaque classe de base ou l’interface s’affiche sur une ligne distincte avec le `inherit` (mot clé).

La définition du type d’une classe abstraite peut contenir des membres entièrement définis, mais elle peut également contenir des membres abstraits. La syntaxe pour les membres abstraits est affichée séparément dans la syntaxe précédente. Dans cette syntaxe, la *signature de type* d’un membre est une liste qui contient les types de paramètre dans l’ordre et les types de retour, séparée par `->` jetons et/ou `*` jetons selon ce qui convient pour curryfiés et basée sur des tuples paramètres. La syntaxe pour les signatures de type de membre abstrait est identique qu’utilisés dans les fichiers de signature et celle indiquée par IntelliSense dans l’éditeur de Code Visual Studio.

Le code suivant illustre une classe abstraite forme, qui dispose de deux classes dérivées non abstraite, carré et un cercle. L’exemple montre comment utiliser les propriétés, méthodes et classes abstraites. Dans l’exemple, la forme de classe abstraite représente les éléments communs des entités concrètes circle et square. Les fonctionnalités communes à toutes les formes (dans un système de coordonnées à deux dimensions) sont abstraites dans la classe de forme : la position sur la grille, un angle de rotation et les propriétés de zone et de périmètre. Celles-ci peuvent être substituées, à l’exception de position, le comportement qui ne peut pas modifier des formes.

La méthode de rotation peut être substituée, comme dans la classe Circle, qui est indifférente à la rotation en raison de sa symétrie. Dans la classe Circle, la méthode de rotation est remplacée par une méthode qui ne fait rien.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Sortie :**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Voir aussi
[Classes](classes.md)

[Membres](members/index.md)

[Méthodes](members/methods.md)

[Propriétés](members/Properties.md)
