---
title: "Comment&#160;: impl&#233;menter de mani&#232;re explicite des membres d&#39;interface (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "interfaces (C#), implémenter de manière explicite"
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Comment&#160;: impl&#233;menter de mani&#232;re explicite des membres d&#39;interface (Guide de programmation C#)
Cet exemple déclare une [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, et une classe, `Box`, qui implémente de façon explicite les membres d'interface `getLength` et `getWidth`.  Les membres sont accessibles via l'instance d'interface `dimensions`.  
  
## Exemple  
 [!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-explicitly-implem_1_1.cs)]  
  
## Programmation fiable  
  
-   Notez que les lignes suivantes, dans la méthode `Main`, sont transformées en commentaires, parce qu'elles produiraient des erreurs de compilation.  Un membre d'interface qui est implémenté de façon explicite n'est pas accessible à partir d'une instance de [classe](../../../csharp/language-reference/keywords/class.md) :  
  
     [!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-explicitly-implem_1_2.cs)]  
  
-   Notez également que les lignes suivantes, dans la méthode `Main`, impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d'une instance de l'interface :  
  
     [!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-explicitly-implem_1_3.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Comment : implémenter de manière explicite des membres de deux interfaces](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)