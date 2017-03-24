---
title: "Comment&#160;: utiliser un dictionnaire pour stocker des instances d&#39;&#233;v&#233;nements (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "événements (C#), stocker des instances dans un dictionnaire"
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Comment&#160;: utiliser un dictionnaire pour stocker des instances d&#39;&#233;v&#233;nements (Guide de programmation&#160;C#)
Une utilisation de `accessor-declarations` consiste à exposer un grand nombre d'événements sans allouer de champ pour chaque événement, mais en utilisant à la place un dictionnaire pour stocker les instances d'événements.  Ceci est utile uniquement si vous disposez de nombreux événements, mais que vous prévoyez que la plupart des événements ne seront pas implémentés.  
  
## Exemple  
 [!code-cs[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)