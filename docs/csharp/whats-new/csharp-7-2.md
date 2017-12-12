---
title: "Nouveautés de C# 7.2"
description: "Vue d’ensemble des nouvelles fonctionnalités de C# 7.2."
keywords: conception de langage C#, 7.2, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a>Nouveautés de C# 7.2

C# 7.2 est une autre version intermédiaire qui ajoute un certain nombre de fonctionnalités utiles.
Cette version a notamment pour but d’utiliser plus efficacement les types valeur en évitant des copies ou allocations inutiles. 

Les fonctionnalités restantes sont des fonctionnalités réduites, mais pratiques.

C# 7.2 utilise l’élément de configuration de [sélection de la version du langage](csharp-7-1.md#language-version-selection) pour sélectionner la version du langage du compilateur.

Les nouvelles fonctionnalités de langage de cette version sont :

* [Sémantique de référence avec les types valeur](#reference-semantics-with-value-types)
  - Une combinaison des améliorations de la syntaxe qui permettent d’utiliser les types valeur avec la sémantique de référence.
* [Arguments nommés non placés en position de fin](#non-trailing-named-arguments)
  - Les arguments nommés peuvent être suivis par des arguments de position.
* [Traits de soulignement de début dans les littéraux numériques](#leading-underscores-in-numeric-literals)
  - Les littéraux numériques peuvent maintenant comporter des traits de soulignement de début avant tout chiffre affiché.
* [Modificateur d’accès `private protected`](#private-protected)
  - Le modificateur d’accès `private protected` active l’accès pour les classes dérivées dans le même assembly.

## <a name="reference-semantics-with-value-types"></a>Sémantique de référence avec les types valeur

Les fonctionnalités de langage introduites dans 7.2 vous permettent de travailler avec les types valeur tout en utilisant la sémantique de référence. Elles sont conçues pour améliorer les performances en réduisant la copie des types valeur sans impliquer les allocations de mémoire associées à l’utilisation des types référence. Les fonctionnalités incluent :

 - Le modificateur `in` sur les paramètres pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée.
 - Le modificateur `ref readonly` sur les retours de méthode pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures sur cet objet.
 - La déclaration `readonly struct` pour indiquer qu’un struct est immuable et doit être passé comme un paramètre `in` aux méthodes de ses membres.
 - La déclaration `ref struct` pour indiquer qu’un type struct accède directement à la mémoire managée et doit toujours être alloué par la pile.

Vous pouvez en savoir plus sur toutes ces modifications dans [Sémantique de référence avec les types valeur](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Arguments nommés non placés en position de fin

Les appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments de position quand ces arguments nommés se trouvent dans les positions appropriées. Pour plus d’informations, consultez [Arguments nommés et facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Traits de soulignement de début dans les littéraux numériques

L’implémentation de la prise en charge des séparateurs numériques dans C# 7.0 n’autorisait pas `_` comme premier caractère de la valeur littérale. Les littéraux numériques binaires et hexadécimaux peuvent maintenant commencer par un caractère `_`. 

Exemple :

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

Enfin, un nouveau modificateur d’accès composé, `private protected`, indique qu’un membre peut être accessible par la classe conteneur ou les classes dérivées qui sont déclarées dans le même assembly. Alors que `protected internal` autorise l’accès par des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclarés dans le même assembly.

Pour plus d’informations, consultez [Modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans Informations de référence sur le langage.
