---
title: "Méthodes (F#)"
description: "Découvrez comment une méthode) (F # est une fonction associée à un type qui sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a>Méthodes

A *méthode* est une fonction qui est associée à un type. Dans la programmation orientée objet, les méthodes sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types.


## <a name="syntax"></a>Syntaxe

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>Remarques
Dans la syntaxe précédente, vous pouvez voir les différentes formes de définitions et déclarations de méthode. Dans le corps de méthode plus longs, un saut de ligne suit le signe égal (=) et le corps de la totalité de la méthode est mise en retrait.

Attributs peuvent être appliqués à une déclaration de méthode. Ils précèdent la syntaxe pour une définition de méthode et sont généralement répertoriés sur une ligne distincte. Pour plus d’informations, consultez [Attributs](../attributes.md).

Les méthodes peuvent être marquées `inline`. Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).

Les méthodes non inline peuvent être utilisées de manière récursive dans le type ; Il n’est pas nécessaire d’utiliser explicitement le `rec` (mot clé).


## <a name="instance-methods"></a>Méthodes d’instance
Méthodes d’instance sont déclarées avec le `member` (mot clé) et un *auto-identificateur*, suivi d’un point (.) et le nom de la méthode et des paramètres. Comme c’est le cas pour `let` liaisons, le *la liste des paramètres* peut être un modèle. En règle générale, vous insérez la méthode paramètres entre parenthèses dans une forme de tuple, qui est les façon dont les méthodes apparaissent en F # lorsqu’ils sont créés dans d’autres langages .NET Framework. Toutefois, le formulaire curryfié (paramètres séparés par des espaces) est également courant et autres modèles sont également pris en charge.

L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Dans les méthodes d’instance, n’utilisez pas l’auto-identificateur pour accéder aux champs définis à l’aide de liaisons let. Utilisez l’auto-identificateur lorsque l’accès à d’autres membres et des propriétés.


## <a name="static-methods"></a>Méthodes statiques
Le mot clé `static` est utilisé pour spécifier qu’une méthode peut être appelée sans une instance et n’est pas associé à une instance d’objet. Sinon, les méthodes sont des méthodes d’instance.

L’exemple dans la section suivante montre les champs déclarés avec le `let` (mot clé), les membres de propriété déclarés avec le `member` (mot clé) et une méthode statique est déclaré avec le `static` (mot clé).

L’exemple suivant illustre la définition et l’utilisation de méthodes statiques. Supposez que ces définitions de méthode se trouvent dans le `SomeType` classe dans la section précédente.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Méthodes abstraites et virtuelles
Le mot clé `abstract` indique qu’une méthode a un emplacement de dispatch virtuel et peut-être pas une définition de la classe. A *emplacement de dispatch virtuel* est une entrée dans une table de fonctions gérée en interne qui est utilisée au moment de l’exécution pour rechercher des fonctions virtuelles appelle dans un type orienté objet. Le mécanisme de dispatch virtuel est le mécanisme qui implémente *le polymorphisme*, une fonctionnalité importante de la programmation orientée objet. Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite*, ce qui signifie qu’aucune instance de cette classe ne peut être créée. Pour plus d’informations sur les classes abstraites, consultez [Classes abstraites](../abstract-classes.md).

Les déclarations de méthode abstraite n’incluent pas de corps de méthode. Au lieu de cela, le nom de la méthode est suivi par un signe deux-points ( :) et une signature de type pour la méthode. La signature de type d’une méthode est identique à celle indiquée par IntelliSense lorsque vous placez le pointeur de la souris sur un nom de méthode dans l’éditeur de Code Visual Studio, à l’exception sans nom de paramètre. Les signatures de type sont également affichées par l’interpréteur, fsi.exe, lorsque vous travaillez de manière interactive. La signature de type d’une méthode est formée en répertoriant les types des paramètres, suivis par le type de retour, avec les symboles de séparateur approprié. Les paramètres curryfiés sont séparés par `->` et les paramètres de tuple sont séparés par `*`. La valeur de retour est toujours séparée des arguments par une `->` symbole. Parenthèses peuvent être utilisées pour grouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer lorsqu’un tuple est traité comme un paramètre unique plutôt que comme deux paramètres.

Vous pouvez également attribuer des définitions par défaut méthodes abstraites en ajoutant la définition à la classe et en utilisant le `default` (mot clé), comme indiqué dans le bloc de syntaxe dans cette rubrique. Une méthode abstraite qui a une définition dans la même classe équivaut à une méthode virtuelle dans d’autres langages .NET Framework. Il existe ou non une définition, le `abstract` (mot clé) crée un nouvel emplacement de dispatch dans la table de fonctions virtuelles pour la classe.

Indépendamment de si une classe de base implémente ses méthodes abstraites, classes dérivées peuvent fournir des implémentations de méthodes abstraites. Pour implémenter une méthode abstraite dans une classe dérivée, définissez une méthode qui a le même nom et la signature dans la classe dérivée, mais utilisez le `override` ou `default` (mot clé) et fournissez le corps de méthode. Les mots clés `override` et `default` exactement la même signification. Utilisez `override` si la nouvelle méthode substitue une implémentation de la classe de base ; Utilisez `default` lorsque vous créez une implémentation dans la même classe que la déclaration abstraite d’origine. N’utilisez pas le `abstract` mot clé dans la méthode qui implémente la méthode déclarée abstraite dans la classe de base.

L’exemple suivant illustre une méthode abstraite `Rotate` qui a une implémentation par défaut, l’équivalent d’une méthode virtuelle .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

L’exemple suivant illustre une classe dérivée qui substitue une méthode de classe de base. Dans ce cas, la substitution modifie le comportement afin que la méthode ne fait rien.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Méthodes surchargées
Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents. En F #, les arguments facultatifs sont généralement utilisées au lieu de méthodes surchargées. Toutefois, les méthodes surchargées sont autorisées dans le langage, autant que les arguments sont sous forme de tuple, curryfiée pas de formulaire.

## <a name="optional-arguments"></a>Arguments facultatifs

À compter de F # 4.1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.  Cela a pour but de faciliter l’interopérabilité avec du code c#.  L’exemple suivant illustre la syntaxe :

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Notez que la valeur transmise pour `DefaultParameterValue` doit correspondre au type d’entrée.  Dans l’exemple ci-dessus, il est un `int`.  Tentative de passer une valeur non entière dans `DefaultParameterValue` entraînera une erreur de compilation.

## <a name="example-properties-and-methods"></a>Exemple : Propriétés et méthodes
L’exemple suivant contient un type qui a des exemples de champs, des fonctions privées, des propriétés et une méthode statique.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Voir aussi
[Membres](index.md)
