---
title: "Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31423"
  - "bc31423"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31423"
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ne peut pas implémenter d'événement, car le type délégué de l'événement ne correspond pas au type délégué de l'événement dans l'interface.  Cette erreur se produit lorsque vous définissez plusieurs événements dans une interface et que vous tentez ensuite de les implémenter ensemble avec le même événement.  Un événement peut implémenter deux ou plusieurs événements seulement si tous les événements implémentés sont déclarés à l'aide de la syntaxe `As` et spécifient le même type délégué.  
  
 **ID d'erreur :** BC31423  
  
### Pour corriger cette erreur  
  
-   Implémentez les événements séparément.  
  
     \- ou \-  
  
-   Définissez les événements dans l'interface à l'aide de la syntaxe `As` et spécifiez le même type délégué.  
  
## Voir aussi  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)