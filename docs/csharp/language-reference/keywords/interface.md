---
title: "interface (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "interface_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "interface (mot clé C#)"
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# interface (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une interface contient uniquement les signatures des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), des [événements](../../../csharp/programming-guide/events/index.md) ou des [indexeurs](../../../csharp/programming-guide/indexers/index.md).  Une classe ou struct qui implémente l'interface doit implémenter les membres de l'interface spécifiés dans la définition d'interface.  Dans l'exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n'a pas de paramètres et retourne `void`.  
  
 Pour plus d'informations et d'exemples, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
## Exemple  
 [!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Une interface peut être membre d'un espace de noms ou d'une classe, et peut contenir les signatures des membres suivants :  
  
-   [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Événements](../../../csharp/language-reference/keywords/event.md)  
  
 Une interface peut hériter d'une ou de plusieurs interfaces de base.  
  
 Si une liste des types de base contient une classe de base et des interfaces, la classe de base doit apparaître en premier dans la liste.  
  
 Une classe qui implémente une interface peut implémenter de façon explicite des membres de cette interface.  Lorsqu'un membre est implémenté de façon explicite, il n'est pas accessible via une instance de classe, mais uniquement via une instance de l'interface.  
  
 Pour d'autres détails et exemples de code sur des implémentations d'interface explicites, consultez [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## Exemple  
 L'exemple ci\-après illustre l'implémentation d'une interface.  Dans cet exemple, l'interface contient la déclaration de propriété et la classe, l'implémentation.  Une instance d'une classe qui implémente `IPoint` a `x` et `y` propriétés entières.  
  
 [!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Utilisation d'indexeurs](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)