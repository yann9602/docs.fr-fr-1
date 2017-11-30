---
title: "Quelles sont les nouveautés dans c# 7.2"
description: "Vue d’ensemble des nouvelles fonctionnalités de c# 7.2."
keywords: Conception du langage c#, 7.2, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a>Quelles sont les nouveautés dans c# 7.2

7.2 c# est un autre point de mise à jour d’ajoute un nombre de fonctionnalités utiles.
Un thème pour cette version fonctionne plus efficacement avec les types valeur en évitant de copies non nécessaires ou des allocations. 

Les fonctionnalités restantes sont petites, agréable pour lesquels des fonctionnalités.

7.2 c# utilise le [sélection de la version linguistique](csharp-7-1.md#language-version-selection) élément de configuration pour sélectionner la version de langue du compilateur.

Les nouvelles fonctionnalités de langage dans cette version sont :

* [Sémantique de référence avec les types valeur](#reference-semantics-with-value-types)
  - Une combinaison des améliorations de la syntaxe qui permettent de travailler avec les types de valeur à l’aide de la sémantique de référence.
* [Arguments nommé non-fin](#non-trailing-named-arguments)
  - Arguments nommés peuvent être suivis par des arguments de position.
* [Début des traits de soulignement dans les littéraux numériques](#leading-underscores-in-numeric-literals)
  - Littéraux numériques peuvent avoir maintenant au début des traits de soulignement avant tous les chiffres imprimés.
* [`private protected`modificateur d’accès](#private-protected)
  - Le `private protected` modificateur d’accès permet l’accès pour les classes dérivées dans le même assembly.

## <a name="reference-semantics-with-value-types"></a>Sémantique de référence avec les types valeur

Les fonctionnalités de langage introduites dans 7.2 vous permettent de travailler avec les types valeur lors de l’utilisation d’une sémantique de référence. Elles sont conçues pour améliorer les performances en réduisant les types valeur copie sans avoir aux allocations de mémoire associées à l’aide des types référence. Les fonctionnalités incluent :

 - Le `in` modificateur de paramètres, pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée.
 - Le `ref readonly` modificateur sur la méthode retourne, pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures à cet objet.
 - Le `readonly struct` déclaration, pour indiquer qu’un struct est immuable et doit être passé comme un `in` paramètre aux méthodes de ses membres.
 - Le `ref struct` déclaration, pour indiquer qu’un type struct accède directement aux mémoire managée et doit toujours être pile allouée.

Vous pouvez en savoir plus sur ces modifications dans [à l’aide de types valeur avec la sémantique de référence](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Arguments nommé non-fin

Appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments positionnels lorsque les arguments nommés se trouvent dans les positions appropriées. Pour plus d’informations, consultez [arguments nommés et optionnels](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Début des traits de soulignement dans les littéraux numériques

L’implémentation de la prise en charge pour les séparateurs de chiffres dans c# 7.0 n’a pas autorisé le `_` pour être le premier caractère de la valeur littérale. Les littéraux numériques binaires et hex peuvent maintenant commencer par une `_`. 

Exemple :

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

Enfin, un modificateur d’accès composés nouvelle : `private protected` indique qu’un membre peut être accessible par les classes dérivées qui sont déclarés dans le même assembly. Alors que `protected internal` autorise l’accès à des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclaré dans le même assembly.

Pour plus d’informations, consultez [les modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans la référence du langage.
