---
title: "base (référence C#)"
description: "Découvrez le mot clé base, qui sert à accéder aux membres de la classe de base à partir d’une classe dérivée en C#."
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords: base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1bbaa0cc05b35f822113bc3a8c3cde966b1484ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="base-c-reference"></a>base (référence C#)

Le mot clé `base` sert à accéder aux membres de la classe de base à partir d’une classe dérivée :

- Il appelle une méthode de la classe de base qui a été substituée par une autre méthode.

- Il spécifie quel constructeur de classe de base doit être appelé lors de la création d’instances de la classe dérivée.

L’accès à une classe de base est autorisé uniquement dans un constructeur, une méthode d’instance ou un accesseur de propriété d’instance.

L’utilisation du mot clé `base` à partir d’une méthode statique est une erreur.

La classe de base accessible est la classe de base spécifiée dans la déclaration de classe. Par exemple, si vous spécifiez `class ClassB : ClassA`, les membres de ClassA sont accessibles à partir de ClassB, quelle que soit la classe de base de ClassA.

## <a name="example"></a>Exemple
Dans cet exemple, la classe de base `Person` et la classe dérivée `Employee` ont toutes les deux une méthode nommée `Getinfo`. En utilisant le mot clé `base`, vous pouvez appeler la méthode `Getinfo` de la classe de base à partir de la classe dérivée.

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Pour obtenir d’autres exemples, consultez [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) et [override](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Exemple
Cet exemple montre comment spécifier le constructeur de classe de base qui est appelé lors de la création d’instances d’une classe dérivée.

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>spécification du langage C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)