---
title: Membres (F#)
description: Membres (F#)
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
translationtype: Human Translation
ms.sourcegitcommit: 0a01ec92a90d99fafaacbd3f71f5177e5cf94a68
ms.openlocfilehash: fe14657b25d122296a6826daba37ea99b6ee64b4
ms.lasthandoff: 04/05/2017

---

# <a name="members"></a>Membres

Cette section décrit les membres de types d’objet F#.


## <a name="remarks"></a>Remarques
Les *membres* sont des fonctionnalités qui font partie d’une définition de type et qui sont déclarées avec le mot clé `member`. Les types d’objet F#, comme les enregistrements, les classes, les unions discriminées, les interfaces et les structures, prennent en charge les membres. Pour plus d’informations, consultez [Enregistrements](../records.md), [Classes](../classes.md), [Unions discriminées](../discriminated-Unions.md), [Interfaces](../interfaces.md) et [Structures](../structures.md).

Les membres constituent en général l’interface publique d’un type ; c’est pourquoi ils sont publics, sauf spécification contraire. Les membres peuvent également être déclarés comme privés ou internes. Pour plus d’informations, consultez [Contrôle d’accès](../access-Control.md). Des signatures peuvent également être utilisées pour les types pour exposer ou ne pas exposer certains membres d’un type. Pour plus d’informations, consultez [Signatures](../signatures.md).

Les champs privés et les liaisons `do`, qui sont uniquement utilisés avec des classes, ne sont pas de vrais membres parce qu’ils ne font jamais partie de l’interface publique d’un type et ne sont pas déclarés avec le mot clé `member`. Toutefois, ils sont décrits dans cette section.


## <a name="related-topics"></a>Rubriques connexes


|Rubrique|Description|
|-----|-----------|
|[Liaisons `let` dans des classes](let-bindings-in-classes.md)|Décrit la définition de champs et de fonctions privés dans des classes.|
|[Liaisons `do` dans des classes](do-bindings-in-classes.md)|Décrit la spécification du code d’initialisation d’objet.|
|[Propriétés](properties.md)|Décrit les membres de propriété dans les classes et d’autres types.|
|[Propriétés indexées](indexed-properties.md)|Décrit les propriétés de type tableau dans des classes et d’autres types.|
|[Méthodes](methods.md)|Décrit les fonctions qui sont membres d’un type.|
|[Constructeurs](constructors.md)|Décrit les fonctions spéciales qui initialisent des objets d’un type.|
|[Surcharge d'opérateur](../operator-overloading.md)|Décrit la définition d’opérateurs personnalisés pour les types.|
|[Événements](events.md)|Décrit la définition d’événements et la prise en charge de la gestion des événements en F#.|
|[Champs explicites : mot clé `val`](explicit-fields-the-val-keyword.md)|Décrit la définition de champs non initialisés dans un type.|

