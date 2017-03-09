---
title: "Handles clause requires a WithEvents variable defined in the containing type or one of its base types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30506"
  - "bc30506"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30506"
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Handles clause requires a WithEvents variable defined in the containing type or one of its base types
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous n'avez pas fourni de variable `WithEvents` dans votre clause `Handles`.  Lorsque le mot clé `Handles` se trouve à la fin d'une déclaration de procédure, cette dernière gère les événements déclenchés par une variable objet déclarée à l'aide du mot clé `WithEvents`.  
  
 **ID d'erreur :** BC30506  
  
### Pour corriger cette erreur  
  
-   Fournissez la variable `WithEvents` nécessaire.  
  
## Voir aussi  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)