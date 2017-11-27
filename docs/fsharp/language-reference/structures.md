---
title: Structures (F#)
description: "En savoir plus sur la structure F #, un type d’objet compact souvent plus efficace qu’une classe pour les types avec une petite quantité de données et un comportement simple."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a>Structures

A *structure* est un type d’objet compact qui peut être plus efficace qu’une classe pour les types qui ont une petite quantité de données et un comportement simple.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a>Remarques
Les structures sont *types valeur*, ce qui signifie qu’elles sont stockées directement sur la pile ou, lorsqu’ils sont utilisés en tant que champs ou éléments de tableau, inline dans le parent de type. Contrairement aux classes et aux enregistrements, les structures ont une sémantique de passage par valeur. Cela signifie qu'elles sont principalement utilisées pour les petits volumes de données qui sont fréquemment sollicités et copiés.

Dans la syntaxe précédente, deux formes sont présentes. La première n'est pas la syntaxe simplifiée, mais elle est néanmoins fréquemment utilisée, car quand vous employez les mots clés `struct` et `end`, vous pouvez omettre l'attribut `StructAttribute` qui apparaît dans la seconde forme. Vous pouvez abréger `StructAttribute` en `Struct`.

Le *éléments de définition de type* dans la syntaxe précédente représente les définitions et déclarations de membre. Les structures peuvent avoir des constructeurs et des champs modifiables et non modifiables, et peuvent déclarer des membres et des implémentations d'interface. Pour plus d’informations, consultez [membres](members/index.md).

Les structures ne peuvent pas participer à l'héritage, ne peuvent pas contenir les liaisons `let` ou `do`, et ne peuvent pas comporter de manière récursive les champs de leur propre type (bien qu'elles puissent contenir des cellules de référence qui référencent leur propre type).

Étant donné que les structures n'autorisent pas les liaisons `let`, vous devez déclarer leurs champs à l'aide du mot clé `val`. Le mot clé `val` définit un champ et son type, mais n'autorise pas l'initialisation. À la place, les déclarations `val` sont initialisées à la valeur zéro ou null. Pour cette raison, les structures ayant un constructeur implicite (c'est-à-dire les paramètres qui sont fournis immédiatement après le nom de la structure dans la déclaration) requièrent que les déclarations `val` soient annotées avec l'attribut `DefaultValue`. Les structures ayant un constructeur défini prennent toujours en charge l'initialisation à zéro. Par conséquent, l'attribut `DefaultValue` est une déclaration selon laquelle une telle valeur égale à zéro est valide pour le champ. Les constructeurs implicites pour les structures n'exécutent aucune action, car les liaisons `let` et `do` ne sont pas autorisées sur le type, mais les valeurs de paramètre de constructeur implicite passées sont disponibles en tant que champs privés.

Les constructeurs explicites peuvent impliquer l'initialisation des valeurs de champ. Quand une structure a un constructeur explicite, elle prend toujours en charge l'initialisation à zéro ; toutefois, vous n'utilisez pas l'attribut `DefaultValue` sur les déclarations `val`, car il est en conflit avec le constructeur explicite. Pour plus d’informations sur `val` déclarations, consultez [champs explicites : le `val` mot clé](members/explicit-fields-the-val-keyword.md).

Les attributs et les modificateurs d'accessibilité sont autorisés sur les structures et suivent les mêmes règles que celles des autres types. Pour plus d’informations, consultez [attributs](attributes.md) et [le contrôle d’accès](access-control.md).

Les exemples de code suivants illustrent des définitions de structure.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>Les enregistrements de struct et les Unions discriminées

À compter de F # 4.1, vous pouvez représenter [enregistrements](records.md) et [les Unions discriminées](discriminated-unions.md) en tant que structures avec le `[<Struct>]` attribut.  Consultez chaque article pour en savoir plus.
    
## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Classes](classes.md)

[Enregistrements](records.md)

[Membres](members/index.md)
