---
title: "partiel, Type (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "partialtype"
  - "partialtype_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "types partiels (C#)"
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# partiel, Type (R&#233;f&#233;rence C#)
Les définitions de type partiel autorisent le fractionnement de la définition d'une classe, d'une structure ou d'une interface en plusieurs fichiers.  
  
 Dans File1.cs :  
  
 [!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/csharp/partial-type_1.cs)]  
  
 Dans File2.cs, la déclaration :  
  
 [!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/csharp/partial-type_2.cs)]  
  
## Notes  
 Le fractionnement d'une classe, d'une structure ou d'un type d'interface sur plusieurs fichiers peut être utile dans le cadre de projets de grande taille ou de code généré automatiquement, comme celui fourni par le [Windows Forms Designer](http://msdn.microsoft.com/fr-fr/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  Un type partiel peut contenir une [méthode partielle](../../../csharp/language-reference/keywords/partial-method.md).  Pour plus d'informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)