---
title: "Comment&#160;: combiner des d&#233;l&#233;gu&#233;s (d&#233;l&#233;gu&#233;s multicast) (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "délégués (C#), combiner"
  - "délégués multicast (C#)"
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Comment&#160;: combiner des d&#233;l&#233;gu&#233;s (d&#233;l&#233;gu&#233;s multicast) (Guide de programmation C#)
Cet exemple explique comment créer des délégués multicast.  Une propriété utile des objets [délégués](../../../csharp/language-reference/keywords/delegate.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l'aide de l'opérateur `+`.  Le délégué multicast contient une liste des délégués assignés.  Lorsque le délégué multicast est appelé, il appelle les délégués dans la liste, dans l'ordre.  Seuls des délégués de même type peuvent être combinés.  
  
 Vous pouvez utiliser l'opérateur `-` pour supprimer un délégué de composant d'un délégué multicast.  
  
## Exemple  
 [!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#11)]  
  
## Voir aussi  
 <xref:System.MulticastDelegate>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)