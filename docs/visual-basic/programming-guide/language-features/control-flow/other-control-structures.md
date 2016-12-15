---
title: "Other Control Structures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "statements [Visual Basic], control flow"
  - "control structures"
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Other Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit des structures de contrôle qui vous permettent de supprimer une ressource ou de réduire le nombre de fois où vous devez répéter une référence d'objet.  
  
## Construction Using...End Using  
 La construction `Using...End Using` établit un bloc d'instructions dans lequel vous utilisez une ressource telle qu'une connexion SQL.  Vous pouvez éventuellement acquérir la ressource avec l'instruction `Using`.  Lorsque vous quittez le bloc `Using`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supprime automatiquement la ressource afin qu'un autre code puisse l'utiliser.  La ressource doit être locale et supprimable.  Pour plus d'informations, consultez [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## With...End With, construction  
 La construction `With...End With` vous permet de spécifier une référence d'objet une fois, puis d'exécuter une série d'instructions qui accèdent à ses membres.  Vous pouvez ainsi simplifier votre code et améliorer les performances puisqu'il n'est pas nécessaire que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rétablisse la référence pour chaque instruction qui accède au code.  Pour plus d'informations, consultez [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## Voir aussi  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)