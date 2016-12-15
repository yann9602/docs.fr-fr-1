---
title: "Statement cannot end a block outside of a line &#39;If&#39; statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32005"
  - "bc32005"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32005"
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Statement cannot end a block outside of a line &#39;If&#39; statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction `If` sur une seule ligne contient plusieurs instructions séparées par des deux\-points \(:\), l'une est une instruction `End` pour un bloc de contrôle en dehors de la ligne unique `If`.  Les instructions `If` sur une seule ligne n'utilisent pas l'instruction `End If`.  
  
 **ID d'erreur :** BC32005  
  
### Pour corriger cette erreur  
  
-   Déplacez cette instruction `If` en dehors du bloc de contrôle qui contient l'instruction `End If`.  
  
## Voir aussi  
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)