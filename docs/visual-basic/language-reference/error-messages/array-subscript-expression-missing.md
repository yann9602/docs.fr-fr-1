---
title: "Array subscript expression missing | Microsoft Docs"
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
  - "bc30306"
  - "vbc30306"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30306"
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array subscript expression missing
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une initialisation de tableau omet un ou plusieurs des indices qui définissent les tailles de tableau.  Par exemple, l'instruction peut contenir l'expression `myArray (5,5,,10)` qui omet le troisième indice.  
  
 **ID d'erreur :** BC30306  
  
### Pour corriger cette erreur  
  
-   Spécifiez l'indice manquant.  
  
## Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)