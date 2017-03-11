---
title: "partielle, m&#233;thode (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "partialmethod_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "méthodes partielles (C#)"
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# partielle, m&#233;thode (R&#233;f&#233;rence&#160;C#)
Une méthode partielle a sa signature définie dans une partie d'un type partiel et son implémentation définie dans une autre partie du type.  Les méthodes partielles permettent aux concepteurs de classes de fournir des raccordements de méthode, semblables aux gestionnaires d'événements, que les développeurs peuvent décider d'implémenter ou non.  Si le développeur ne fournit pas d'implémentation, le compilateur supprime la signature à la compilation.  Les conditions suivantes s'appliquent aux méthodes partielles :  
  
-   Les signatures dans les deux parties du type partiel doivent correspondre.  
  
-   La méthode doit retourner void.  
  
-   Aucun modificateur d'accès n'est autorisé.  Les méthodes partielles sont implicitement privées.  
  
 L'exemple suivant présente une méthode partielle définie dans deux parties d'une classe partielle :  
  
 [!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/csharp/partial-method_1.cs)]  
  
 Pour plus d'informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [partiel, Type](../../../csharp/language-reference/keywords/partial-type.md)