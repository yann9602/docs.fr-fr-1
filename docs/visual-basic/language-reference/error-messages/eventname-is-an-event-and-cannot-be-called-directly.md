---
title: "&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32022"
  - "vbc32022"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32022"
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

'\<`eventname`\>' est un événement et ne peut donc pas être appelé directement.  Utilisez une instruction `RaiseEvent` pour déclencher un événement.  
  
 Un appel de procédure spécifie un événement pour le nom de la procédure.  Un gestionnaire d'événements est une procédure, mais l'événement lui\-même est un moyen de signalisation qui doit être déclenché et géré.  
  
 **ID d'erreur :** BC32022  
  
### Pour corriger cette erreur  
  
1.  Utilisez une instruction `RaiseEvent` pour signaler un événement et appeler les procédures qui le gèrent.  
  
## Voir aussi  
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)