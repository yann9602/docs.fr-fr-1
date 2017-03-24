---
title: "Resume without error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID20"
dev_langs: 
  - "VB"
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Resume without error
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une instruction `Resume` est apparue en dehors du code de gestion des erreurs ou le code est passé dans un gestionnaire d'erreurs bien qu'il n'y ait pas eu d'erreur.  
  
### Pour corriger cette erreur  
  
1.  Déplacez l'instruction `Resume`dans un gestionnaire d'erreurs ou supprimez\-la.  
  
2.  Les passages à des étiquettes sont impossibles à travers les procédures. Par conséquent, cherchez dans la procédure l'étiquette qui identifie le gestionnaire d'erreurs.  Si vous trouvez une étiquette dupliquée spécifiée comme cible d'une instruction `GoTo` et qui n'est pas une instruction `On Error GoTo`, changez l'étiquette de ligne de manière à ce qu'elle corresponde à la cible attendue.  
  
## Voir aussi  
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)