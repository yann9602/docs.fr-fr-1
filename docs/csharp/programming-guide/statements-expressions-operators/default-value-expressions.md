---
title: "Expressions de valeur par défaut (Guide de programmation C#)"
description: "Les expressions de valeur par défaut produisent la valeur par défaut des types référence et des types valeur"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="default-value-expressions-c-programming-guide"></a>Expressions de valeur par défaut (Guide de programmation C#)

Une expression de valeur par défaut produit la valeur par défaut d’un type. Les expressions de valeur par défaut sont particulièrement utiles dans les méthodes et classes génériques. Le problème qui se pose avec l’utilisation des génériques est de savoir comment assigner une valeur par défaut à un type paramétrable `T` quand vous ne connaissez pas les éléments suivants à l’avance :

- Si `T` est un type référence ou un type valeur.
- Si `T` est un type valeur, s’il s’agit d’une valeur numérique ou d’un struct défini par l’utilisateur.

 Avec une variable `t` d’un type paramétré `T`, l’instruction `t = null` est valide uniquement si `T` est un type référence. L’affectation de `t = 0` fonctionne uniquement pour les types valeur numériques mais pas pour les structs. La solution consiste à utiliser une expression de valeur par défaut, qui retourne `null` pour les types référence (types de classes et types interface) et zéro pour les types valeur numériques. Pour des structs définis par l’utilisateur, elle retourne le struct initialisé sur le modèle de bit zéro qui produit 0 ou `null` pour chaque membre, selon que ce membre est un type valeur ou référence. Pour les types valeur Nullable, `default` retourne <xref:System.Nullable%601?displayProperty=fullName>, initialisé comme n’importe quel struct.

L’expression `default(T)` n’est pas limitée aux classes et aux méthodes génériques. Vous pouvez utiliser les expressions de valeur par défaut avec n’importe quel type managé. Toutes ces expressions sont valides :

 [!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 L’exemple suivant de la classe `GenericList<T>` montre comment utiliser l’opérateur `default(T)` dans une classe générique. Pour plus d’informations, consultez [Introduction aux génériques](../generics/introduction-to-generics.md).

 [!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Littéral par défaut et inférence de type

À partir de C# 7.1, vous pouvez utiliser les littéraux `default` pour les expressions de valeur par défaut quand le compilateur peut déduire le type de l’expression. Le littéral `default` génère la même valeur que l’équivalent `default(T)`, où `T` est le type déduit. Vous pouvez ainsi alléger votre code en réduisant la redondance de déclarer un type plusieurs fois. Vous pouvez utiliser le littéral `default` dans l’un des emplacements suivants :

- initialiseur de variable
- assignation de variable
- déclaration de la valeur par défaut d’un paramètre facultatif
- valeur pour un argument d’appel de méthode
- instruction return (ou expression dans un membre expression-bodied)

L’exemple suivant illustre plusieurs utilisations du littéral `default` dans une expression de valeur par défaut :

[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Voir aussi

 <xref:System.Collections.Generic> [Guide de programmation C#](../index.md)   
 [Génériques](../generics/index.md)   
 [Méthodes génériques](../generics/generic-methods.md)   
 [Génériques](~/docs/standard/generics/index.md)   

