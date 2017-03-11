---
title: "How to: Refer to the Current Instance of an Object (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], object"
  - "objects [Visual Basic], referring to current instance"
  - "instances, referring to current"
  - "current instance"
  - "object variables"
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Refer to the Current Instance of an Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'*instance en cours* d'un objet est celle dans laquelle le code est en train de s'exécuter.  
  
 Vous utilisez le mot clé `Me` pour faire référence à l'instance actuelle.  
  
### Pour faire référence à l'instance en cours  
  
-   Utilisez le mot clé `Me` où vous utiliseriez normalement le nom d'une variable objet.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Bien que `Me` se comporte comme une variable objet, vous ne pouvez pas le déclarer ni lui assigner quoi que ce soit.  `Me` fait toujours référence à l'instance actuelle.  
  
## Voir aussi  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)