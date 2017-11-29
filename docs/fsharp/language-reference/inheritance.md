---
title: "Héritage (F#)"
description: "Découvrez comment spécifier des relations d’héritage F # à l’aide du mot clé 'inherit'."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a>Héritage

L’héritage est utilisé pour modéliser la relation « est-un », ou sous-typage, dans la programmation orientée objet.


## <a name="specifying-inheritance-relationships"></a>Spécification de relations d’héritage
Vous spécifiez des relations d’héritage à l’aide de la `inherit` mot clé dans une déclaration de classe. La forme syntaxique de base est illustrée dans l’exemple suivant.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Une classe peut avoir au plus une classe de base directe. Si vous ne spécifiez pas une classe de base à l’aide de la `inherit` (mot clé), la classe hérite implicitement de `System.Object`.


## <a name="inherited-members"></a>Membres hérités
Si une classe hérite d’une autre classe, les méthodes et les membres de la classe de base sont disponibles pour les utilisateurs de la classe dérivée, comme si elles étaient des membres directs de la classe dérivée.

Les liaisons let et les paramètres du constructeur sont privés à une classe et, par conséquent, ne peut pas être accessible à partir de classes dérivées.

Le mot clé `base` est disponible dans les classes dérivées et fait référence à l’instance de la classe de base. Il est utilisé comme auto-identificateur.


## <a name="virtual-methods-and-overrides"></a>Les méthodes virtuelles et remplacements
Méthodes virtuelles (et les propriétés) fonctionnent différemment en F # par rapport aux autres langages .NET. Pour déclarer un nouveau membre virtuel, vous utilisez la `abstract` (mot clé). Pour cela, indépendamment de si vous fournissez une implémentation par défaut de cette méthode. Par conséquent, une définition complète d’une méthode virtuelle dans une classe de base suit ce modèle :

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

Et, dans une classe dérivée, une substitution de cette méthode virtuelle suit ce modèle :

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Si vous omettez l’implémentation par défaut dans la classe de base, la classe de base est une classe abstraite.

L’exemple de code suivant illustre la déclaration d’une nouvelle méthode virtuelle `function1` dans une classe de base et comment la substituer dans une classe dérivée.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>Constructeurs et héritage
Le constructeur de la classe de base doit être appelé dans la classe dérivée. Les arguments du constructeur de classe de base apparaissent dans la liste d’arguments dans le `inherit` clause. Les valeurs qui sont utilisées doivent être déterminées à partir des arguments fournis au constructeur de classe dérivée.

Le code suivant montre une classe de base et une classe dérivée, où la classe dérivée appelle le constructeur de classe de base dans la clause d’héritage :

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

Dans le cas de plusieurs constructeurs, le code suivant peut être utilisé. La première ligne des constructeurs de classe dérivée est la `inherit` clause et les champs s’affichent en tant que champs explicites qui sont déclarées avec le `val` (mot clé). Pour plus d’informations, consultez [champs explicites : le `val` mot clé](members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternatives à l’héritage
Dans le cas où une modification mineure d’un type est requise, envisagez d’utiliser une expression d’objet en guise d’alternative à l’héritage. L’exemple suivant illustre l’utilisation d’une expression d’objet en guise d’alternative à la création d’un type dérivé :

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Pour plus d’informations sur les expressions d’objet, consultez [Expressions d’objet](object-expressions.md).

Lorsque vous créez des hiérarchies d’objets, envisagez d’utiliser une union discriminée au lieu de l’héritage. Les unions discriminées peuvent également comportement du modèle variée des différents objets qui partagent un type global commun. Une union discriminée unique peut souvent supprimer la nécessité pour un nombre de classes dérivées qui sont des variations mineures de l’autre. Pour plus d’informations sur les unions discriminées, consultez [les Unions discriminées](discriminated-unions.md).


## <a name="see-also"></a>Voir aussi
[Expressions d'objet](object-expressions.md)

[Informations de référence du langage F#](index.md)
