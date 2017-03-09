---
title: "explicit (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "explicit_CSharpKeyword"
  - "explicit"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "explicit (mot clé C#)"
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# explicit (r&#233;f&#233;rence C#)
Le mot clé `explicit` déclare un opérateur de conversion de type défini par l'utilisateur qui doit être appelé avec un cast.  Par exemple, cet opérateur convertit d'une classe appelée Fahrenheit en une classe appelée Celsius :  
  
 [!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_1.cs)]  
  
 Cet opérateur de conversion peut être appelé comme suit :  
  
 [!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_2.cs)]  
  
 L'opérateur de conversion convertit un type source en type cible.  Le type source fournit l'opérateur de conversion.  À la différence de la conversion implicite, les opérateurs de conversion explicite doivent être appelés au moyen d'une conversion.  Si une opération de conversion risque de provoquer des exceptions ou de perdre des informations, vous devez la marquer comme `explicit`.  Ceci empêche le compilateur d'appeler en mode silencieux l'opération de conversion, ce qui pourrait entraîner des conséquences imprévisibles.  
  
 L'omission d'une conversion entraîne l'erreur de compilation CS0266.  
  
 Pour plus d’informations, consultez [Utilisation d'opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## Exemple  
 L'exemple suivant fournit une classe `Fahrenheit` et une classe `Celsius`, chacune fournissant un opérateur de conversion explicite à l'autre classe.  
  
 [!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_3.cs)]  
  
## Exemple  
 L'exemple ci\-dessous définit un struct, `Digit`, qui représente un seul chiffre décimal.  Un opérateur est défini pour des conversions de `byte` à `Digit`, et comme tous les octets ne peuvent pas être convertis en `Digit`, la conversion est explicite.  
  
 [!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [implicites](../../../csharp/language-reference/keywords/implicit.md)   
 [d'opérateur](../../../csharp/language-reference/keywords/operator.md)   
 [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)   
 [Conversions explicites définies par l'utilisateur liées en C\#](http://go.microsoft.com/fwlink/?LinkId=112384)