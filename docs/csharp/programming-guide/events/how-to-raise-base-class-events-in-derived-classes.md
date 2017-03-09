---
title: "Comment&#160;: d&#233;clencher les &#233;v&#233;nements de la classe de base dans les classes d&#233;riv&#233;es (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "événements (C#), dans des classes dérivées"
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# Comment&#160;: d&#233;clencher les &#233;v&#233;nements de la classe de base dans les classes d&#233;riv&#233;es (Guide de programmation C#)
L'exemple simple suivant illustre la méthode standard pour déclarer des événements dans une classe de base afin qu'ils puissent également être déclenchés à partir de classes dérivées.  Ce modèle est largement utilisé dans les classes Windows Forms de la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  
  
 Lors de la création d'une classe pouvant être utilisée comme classe de base pour d'autres classes, vous devez tenir compte du fait que les événements constituent un type particulier de délégués, ne pouvant être appelés qu'à partir de la classe qui les a déclarés.  Les classes dérivées ne peuvent pas appeler directement les événements déclarés dans la classe de base.  Même si, quelquefois, vous pouvez souhaiter qu'un événement ne puisse être déclenché que par la classe de base, dans la plupart des cas, vous devez permettre à la classe dérivée d'appeler les événements de la classe de base.  À cette fin, vous pouvez créer une méthode d'appel protégée dans la classe de base qui encapsule l'événement.  En appelant ou en remplaçant cette méthode d'appel, les classes dérivées peuvent appeler indirectement l'événement.  
  
> [!NOTE]
>  Ne déclarez pas des événements virtuels dans une classe de base et ne les substituez pas dans une classe dérivée.  Le compilateur c\# ne gère pas correctement et il est impossible de prédire si un abonné à l'événement dérivé s'abonnera effectivement à l'événement de classe de base.  
  
## Exemple  
 [!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/csharp/how-to-raise-base-class-_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Création de gestionnaires d'événements dans les Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)