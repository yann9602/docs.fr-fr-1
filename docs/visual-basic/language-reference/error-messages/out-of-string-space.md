---
title: "Out of string space (Visual Basic) | Microsoft Docs"
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
  - "vbrID14"
dev_langs: 
  - "VB"
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Out of string space (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic vous permet d'utiliser de très grandes chaînes.  Toutefois, les exigences d'autres programmes et la manière dont vous utilisez vos chaînes peuvent provoquer cette erreur.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu'une expression nécessitant la création d'une chaîne temporaire lors de l'évaluation ne déclenche pas l'erreur.  
  
2.  Supprimez de la mémoire toutes les applications dont vous n'avez pas besoin afin de créer de l'espace supplémentaire.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [String Manipulation Summary](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)