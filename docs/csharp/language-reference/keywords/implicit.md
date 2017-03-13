---
title: "implicit (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "implicit"
  - "implicit_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "implicit (mot clé C#)"
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# implicit (r&#233;f&#233;rence C#)
Le mot clé `implicit` est utilisé pour déclarer un opérateur de conversion implicite défini par l'utilisateur.  Utilisez\-le pour permettre les conversions implicites entre un type défini par l'utilisateur et un autre type, s'il est garanti que la conversion ne provoquera pas de perte de données.  
  
## Exemple  
 [!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 En éliminant des conversions superflues, les conversions implicites permettent d'améliorer la lisibilité du code source.  Toutefois, comme les conversions implicites ne requièrent pas que les programmeurs effectuent explicitement un cast d'un type vers l'autre, il faut prendre soin d'empêcher les résultats inattendus.  En général, les opérateurs de conversion implicite ne devraient jamais lever d'exceptions et ne jamais perdre d'informations, afin qu'elles soient utilisées de façon sûre sans que le programmeur ait à intervenir.  Si un opérateur de conversion ne répond pas à ces critères, il doit être marqué comme `explicit`.  Pour plus d'informations, consultez [Utilisation d'opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [explicites](../../../csharp/language-reference/keywords/explicit.md)   
 [d'opérateur](../../../csharp/language-reference/keywords/operator.md)   
 [Comment : implémenter des conversions définies par l'utilisateur entre des structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)