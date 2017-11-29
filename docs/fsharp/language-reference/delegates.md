---
title: "Délégués (F#)"
description: "Apprenez à utiliser avec les délégués en F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a>Délégués

Un délégué représente un appel de fonction en tant qu’objet. En F #, vous devez normalement utiliser des valeurs de fonction pour représenter des fonctions comme valeurs de première classe ; Toutefois, les délégués sont utilisés dans le .NET Framework et ils sont nécessaires lorsque vous interagissez avec les API qui attendent les. Ils peuvent également être utilisés lors de la création de bibliothèques conçues pour utiliser d’autres langages .NET Framework.


## <a name="syntax"></a>Syntaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Remarques
Dans la syntaxe précédente, `type1` représente le type d’argument ou les types et `type2` représente le type de retour. Les types d’arguments qui sont représentées par `type1` sont automatiquement curryfiés. Cela signifie que pour ce type que vous utilisez une forme de tuple si les arguments de la fonction cible sont curryfiés et un tuple entre parenthèses pour les arguments qui sont déjà sous la forme de tuple. La curryfication automatique supprime un jeu de parenthèses, laissant un argument de tuple qui correspond à la méthode cible. Reportez-vous à l’exemple de code pour la syntaxe à utiliser dans chaque cas.

Les délégués peuvent être attachés à des valeurs de fonction F # et statiques ou méthodes d’instance. Les valeurs de fonction F # peuvent être passées directement en tant qu’arguments aux constructeurs délégués. Pour une méthode statique, vous construisez le délégué en utilisant le nom de la classe et la méthode. Pour une méthode d’instance, vous fournissez l’instance d’objet et la méthode dans un seul argument. Dans les deux cas, le membre opérateur d’accès (`.`) est utilisé.

Le `Invoke` méthode sur le type délégué appelle la fonction encapsulée. En outre, les délégués peuvent être passés en tant que valeurs de fonction en référençant le nom de la méthode Invoke sans les parenthèses.

Le code suivant illustre la syntaxe pour créer des délégués qui représentent les différentes méthodes dans une classe. Selon si la méthode est une méthode statique ou une méthode d’instance, et qu’il possède des arguments sous la forme de tuple ou de la forme curryfiée, la syntaxe de déclaration et l’assignation du délégué est un peu différente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Le code suivant illustre certaines des différentes méthodes que vous pouvez utiliser des délégués.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

La sortie de l’exemple de code précédent est comme suit.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Paramètres et arguments](parameters-and-arguments.md)

[Événements](members/events.md)
