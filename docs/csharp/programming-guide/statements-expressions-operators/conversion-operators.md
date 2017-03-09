---
title: "Op&#233;rateurs de conversion (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C#, opérateurs de conversion"
  - "opérateurs de conversion (C#)"
  - "opérateurs (C#), conversion"
  - "conversions définies par l’utilisateur (C#)"
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# Op&#233;rateurs de conversion (Guide de programmation C#)
C\# permet aux programmeurs de déclarer des conversions sur les classes ou les structures afin d'autoriser les conversions dans les deux sens entre ces dernières et d'autres classes, d'autres structures ou des types de base.  Les conversions sont définies comme des opérateurs et nommées en fonction du type vers lequel s'effectue l'opération.  Soit le type de l'argument à convertir, soit le type du résultat de la conversion, mais pas les deux, doit être le type conteneur.  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/conversion-operators_1.cs)]  
  
## Vue d'ensemble des opérateurs de conversion  
 Les opérateurs de conversion ont les propriétés suivantes :  
  
-   Les conversions déclarées comme `implicit` se produisent automatiquement, le cas échéant.  
  
-   Les conversions déclarées comme `explicit` nécessitent qu'un cast soit appelé.  
  
-   Toutes les conversions doivent être déclarées comme `static`.  
  
## Rubriques connexes  
 Pour plus d'informations :  
  
-   [Utilisation d'opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicites](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicites](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [statiques](../../../csharp/language-reference/keywords/static.md)  
  
## Voir aussi  
 <xref:System.Convert>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Conversions explicites définies par l'utilisateur liées en C](http://go.microsoft.com/fwlink/?LinkId=112384)