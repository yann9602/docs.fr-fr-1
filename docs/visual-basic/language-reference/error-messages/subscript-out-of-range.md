---
title: "Subscript out of range (Visual Basic) | Microsoft Docs"
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
  - "vbrID9"
dev_langs: 
  - "VB"
ms.assetid: d0344a65-ec02-4caf-8d3c-9977392ca353
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Subscript out of range (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un indice de tableau n'est pas valide car il se situe en dehors de la plage autorisée.  La plus petite valeur d'indice d'une dimension correspond toujours à 0 et la plus grande valeur d'indice est retournée par la méthode `GetUpperBound` de cette dimension.  
  
### Pour corriger cette erreur  
  
-   Modifiez l'indice de sorte qu'il se situe dans la plage valide.  
  
## Voir aussi  
 <xref:System.Array.GetUpperBound%2A?displayProperty=fullName>   
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)