---
title: "Comment&#160;: impl&#233;menter des conversions d&#233;finies par l&#39;utilisateur entre des structs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions définies par l'utilisateur (C#)"
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# Comment&#160;: impl&#233;menter des conversions d&#233;finies par l&#39;utilisateur entre des structs (Guide de programmation C#)
L'exemple suivant définit deux structures, `RomanNumeral` et `BinaryNumeral`, et décrit les conversions entre ces deux structures.  
  
## Exemple  
 [!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-implement-user-de_1.cs)]  
  
## Programmation fiable  
  
-   Dans l'exemple précédent, l'instruction :  
  
     [!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-implement-user-de_2.cs)]  
  
     convertit un `RomanNumeral` en `BinaryNumeral`.  Étant donné qu'il n'existe pas de conversion directe de `RomanNumeral` vers `BinaryNumeral`, un cast est utilisé pour convertir un `RomanNumeral` en un `int` et un autre cast pour convertir ce dernier en un `BinaryNumeral`.  
  
-   L'instruction  
  
     [!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-implement-user-de_3.cs)]  
  
     convertit un `BinaryNumeral` en `RomanNumeral`.  Étant donné que `RomanNumeral` définit une conversion implicite d'un `BinaryNumeral`, aucun cast n'est requis.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Conversion, opérateurs](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)