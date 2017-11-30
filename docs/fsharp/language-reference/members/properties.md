---
title: "Propriétés (F#)"
description: "En savoir plus sur les propriétés F #, qui sont des membres qui représentent des valeurs associées à un objet."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a>Propriétés

*Propriétés* sont des membres qui représentent des valeurs associées à un objet.


## <a name="syntax"></a>Syntaxe

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Remarques
Propriétés représentent la » a une « relation dans la programmation orientée objet, représentant les données qui sont associés à des instances d’objet ou, pour les propriétés statiques, avec le type.

Vous pouvez déclarer des propriétés de deux façons, selon que vous souhaitez spécifier explicitement la valeur sous-jacente (également appelée magasin de stockage) pour la propriété, ou si vous souhaitez permettre au compilateur de générer automatiquement le magasin de stockage pour vous. En règle générale, vous devez utiliser le mode plus explicite si la propriété a une implémentation non triviale et automatique lorsque la propriété est un simple wrapper simple pour une valeur ou une variable. Pour déclarer une propriété explicitement, utilisez le `member` (mot clé). Cette syntaxe déclarative est suivie par la syntaxe qui spécifie le `get` et `set` méthodes, également nommés *accesseurs*. Les différentes formes de la syntaxe explicite indiquée dans la section syntaxe sont utilisées pour les propriétés en lecture/écriture, en lecture seule et en écriture seule. Pour les propriétés en lecture seule, vous définissez uniquement un `get` méthode ; définir uniquement pour les propriétés en écriture seule, un `set` (méthode). Notez que lorsqu’une propriété a à la fois `get` et `set` accesseurs, l’autre syntaxe vous permet de spécifier les attributs et les modificateurs d’accessibilité qui sont différents pour chaque accesseur, comme indiqué dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Pour les propriétés en lecture/écriture, qui ont à la fois un `get` et `set` (méthode), l’ordre des `get` et `set` peuvent être inversées. Vous pouvez également fournir la syntaxe indiquée pour `get` uniquement et la syntaxe indiquée pour `set` uniquement, au lieu d’utiliser la syntaxe combinée. Cela facilite Commentez la personne `get` ou `set` (méthode), si cela vous peuvent s’avérer nécessaires. Cette solution à l’aide de la syntaxe combinée est indiquée dans le code suivant.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Cette suspension les données pour les propriétés sont appelées des valeurs privé *magasins de stockage*. Pour indiquer au compilateur de créer le magasin de stockage automatiquement, utilisez les mots clés `member val`, omettez l’auto-identificateur, puis indiquez une expression pour initialiser la propriété. Si la propriété doit être mutable, inclure `with get, set`. Par exemple, le type de classe suivant inclut deux propriétés implémentées automatiquement. `Property1`est en lecture seule et est initialisée à l’argument fourni pour le constructeur principal, et `Property2` est une propriété définissable initialisée avec une chaîne vide :

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Propriétés implémentées automatiquement font partie de l’initialisation d’un type, afin qu’ils doivent figurer avant les autres définitions de membre, comme `let` liaisons et `do` liaisons dans une définition de type. Notez que l’expression qui initialise une propriété implémentée automatiquement n’est évaluée que lors de l’initialisation, et pas chaque fois que la propriété est accessible. Ce comportement diffère du comportement d’une propriété implémentée explicitement. Cela efficacement signifie que le code d’initialisation de ces propriétés est ajouté au constructeur de classe. Prenons le code suivant qui illustre cette différence :

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**Sortie**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

La sortie du code précédent montre que la valeur de AutoProperty est inchangée lorsqu’elle est appelée à plusieurs reprises, tandis que le ExplicitProperty change chaque fois qu’elle est appelée. Cela montre que l’expression pour une propriété implémentée automatiquement n’est pas évaluée chaque fois, est la méthode d’accesseur Get de la propriété explicite.


>[!WARNING]
Il existe certaines bibliothèques, telles que Entity Framework (`System.Data.Entity`) qui effectuent des opérations personnalisées dans les constructeurs de classe de base qui ne fonctionnent pas correctement avec l’initialisation des propriétés implémentées automatiquement. Dans ce cas, essayez d’utiliser des propriétés explicites.

Propriétés peuvent être membres de classes, structures, unions discriminées, les enregistrements, interfaces et des extensions de type et peuvent également être définies dans les expressions d’objet.

Attributs peuvent être appliqués aux propriétés. Pour appliquer un attribut à une propriété, écrire l’attribut sur une ligne distincte avant que la propriété. Pour plus d’informations, consultez [Attributs](../attributes.md).

Par défaut, les propriétés sont publiques. Les modificateurs d’accessibilité peuvent également être appliqués aux propriétés. Pour appliquer un modificateur d’accessibilité, ajoutez-le immédiatement avant le nom de la propriété si elle est destinée à appliquer à la fois à la `get` et `set` méthodes ; avant d’ajouter le `get` et `set` mots clés si une accessibilité différente est obligatoire pour chaque accesseur. Le *modificateur d’accessibilité* peut prendre l’une des opérations suivantes : `public`, `private`, `internal`. Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).

Les implémentations de propriété sont exécutées chaque fois qu’une propriété est accessible.


## <a name="static-and-instance-properties"></a>Statique et les propriétés de l’Instance
Propriétés peuvent être statiques ou des propriétés de l’instance. Propriétés statiques peuvent être appelées sans une instance et sont utilisées pour les valeurs associées de type, pas avec des objets individuels. Pour les propriétés statiques, omettez l’auto-identificateur. L’auto-identificateur est requis pour les propriétés de l’instance.

La définition de propriété statique suivante est basée sur un scénario dans lequel vous avez un champ statique `myStaticValue` qui est le magasin de stockage pour la propriété.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Propriétés peuvent également être de type de tableau, auquel cas elles sont appelées *propriétés indexées*. Pour plus d’informations, consultez [propriétés indexées](indexed-properties.md).


## <a name="type-annotation-for-properties"></a>Annotation de type pour les propriétés
Dans de nombreux cas, le compilateur dispose de suffisamment d’informations pour déduire le type d’une propriété du type de magasin de stockage, mais vous pouvez définir explicitement le type en ajoutant une annotation de type.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>À l’aide de la propriété d’accesseurs set
Vous pouvez définir des propriétés qui fournissent des `set` accesseurs à l’aide de la `<-` opérateur.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

La sortie est **20**.


## <a name="abstract-properties"></a>Propriétés abstraites
Propriétés peuvent être abstract. Comme avec les méthodes, `abstract` signifie simplement qu’il existe un dispatch virtuel est associé à la propriété. Propriétés abstraites peuvent être vraiment abstraites, autrement dit, sans une définition dans la même classe. La classe qui contient une telle propriété est par conséquent une classe abstraite. Vous pouvez également abstraite peut simplement signifie qu’une propriété est virtuelle, et dans ce cas, une définition doit être présente dans la même classe. Notez que les propriétés abstraites ne doivent pas être privées, et si un accesseur est abstrait, l’autre doit également être abstract. Pour plus d’informations sur les classes abstraites, consultez [Classes abstraites](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Voir aussi
[Membres](index.md)

[Méthodes](methods.md)
