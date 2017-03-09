---
title: "Declaration expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30188"
  - "bc30188"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30188"
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Declaration expected
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une instruction non déclarative, telle qu'une assignation ou une instruction de boucle, apparaît à l'extérieur de toute procédure.  Seules les déclarations sont autorisées à l'extérieur des procédures.  
  
 En outre, un élément de programmation est déclaré sans mot clé de déclaration, tel que `Dim` ou `Const`.  
  
 **ID d'erreur :** BC30188  
  
### Pour corriger cette erreur  
  
-   Déplacez l'instruction non déclarative vers le corps d'une procédure.  
  
-   Commencez la déclaration par un mot clé de déclaration approprié.  
  
-   Vérifiez si un mot clé de déclaration est mal orthographié.  
  
## Voir aussi  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)