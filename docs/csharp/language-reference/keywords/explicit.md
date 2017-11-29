---
title: "explicit (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords: explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2661f46d79b13808bfb169bfbfffc1a17b866b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-c-reference"></a>explicit (référence C#)
Le mot clé `explicit` déclare un opérateur de conversion de type défini par l’utilisateur qui doit être appelé avec un cast. Par exemple, cet opérateur effectue une conversion d’une classe nommée Fahrenheit vers une classe nommée Celsius :  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 Cet opérateur de conversion peut être appelé comme suit :  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 L’opérateur de conversion convertit un type source en type cible. Le type source fournit l’opérateur de conversion. Contrairement à une conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d’un cast. Si une opération de conversion peut provoquer des exceptions ou la perte d’informations, vous devez la marquer comme `explicit`. Cela empêche que le compilateur appelle l’opération de conversion en mode silencieux, avec éventuellement des conséquences imprévisibles.  
  
 L’omission du cast provoque l’erreur de compilation CS0266.  
  
 Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant fournit des classes `Fahrenheit` et `Celsius`, chacune fournissant un opérateur de conversion explicite à l’autre classe.  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un struct, `Digit`, qui représente un seul chiffre décimal. Un opérateur est défini pour les conversions de `byte` à `Digit`, mais étant donné que les octets ne peuvent pas tous être convertis en `Digit`, la conversion est explicite.  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Conversions explicites définies par l’utilisateur chaînées en C#](http://go.microsoft.com/fwlink/?LinkId=112384)
