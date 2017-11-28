---
title: "Structs C# - Visite guidée du langage C#"
description: "Apprendre les bases des types valeur de C#, appelés structs"
keywords: .NET, C#, struct, type valeur
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="structs"></a>Structs

Comme les classes, les ***structs*** sont des structures de données qui peuvent contenir des membres de données et des fonctions membres. Mais contrairement aux classes, les structures sont des types valeur et ne nécessitent pas d’allocation de tas. Une variable de type struct stocke directement les données de la structure, alors qu’une variable de type class stocke une référence à un objet alloué dynamiquement. Les types struct ne prennent pas en charge l’héritage spécifié par l’utilisateur, et tous les types struct héritent implicitement du type <xref:System.ValueType>, qui à son tour hérite implicitement de `object`.

Les structures sont particulièrement utiles pour les petites structures de données qui ont une sémantique par rapport à leurs valeurs. Les nombres complexes, les points dans un système de coordonnées ou les paires clé-valeur dans un dictionnaire sont de bons exemples de structures. L’utilisation de structures plutôt que de classes pour les petites structures de données peut faire une grande différence dans le nombre d’allocations de mémoire effectuées par une application. Par exemple, le programme suivant crée et initialise un tableau de 100 points. Avec `Point` implémenté en tant que classe, 101 objets séparés sont instanciés : un pour le tableau et un pour chacun des 100 éléments.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Une alternative consiste à faire du Point une struct.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Maintenant, un seul objet est instancié, celui du tableau, et les instances `Point` sont stockées à la suite dans le tableau.

Vous appelez les constructeurs de struct avec l’opérateur new, mais cela n’implique pas que la mémoire est allouée. Au lieu d’allouer dynamiquement un objet et de renvoyer une référence à cet objet, un constructeur de struct retourne simplement la valeur du struct (généralement dans un emplacement temporaire sur la pile), et cette valeur est ensuite copiée si nécessaire.

Avec les classes, deux variables peuvent faire référence au même objet et, par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable. Avec les structs, les variables disposent chacune de leur propre copie des données, et il n’est pas possible pour les opérations sur une d’affecter les autres. Par exemple, la sortie générée par le code suivant varie selon que Point est une classe ou une structure.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Si `Point` est une classe, la sortie est de 20, car a et b font référence au même objet. Si Point est un struct, le résultat est 10, car l’attribution de `a` à `b` crée une copie de la valeur, et cette copie n’est pas affectée par l’assignation consécutive de `a.x`.

L’exemple précédent illustre deux des limitations des structs. Tout d’abord, la copie d’un struct entier est généralement moins efficace que la copie d’une référence d’objet, aussi le passage de paramètres d’affectation et de valeur peut être plus coûteux avec les structures qu’avec les types référence. Ensuite, à l’exception des paramètres `ref` et `out`, il n’est pas possible de créer des références aux structures, ce qui rend leur utilisation impossible dans un certain nombre de situations.

>[!div class="step-by-step"]
[Précédent](classes-and-objects.md)
[Suivant](arrays.md)
