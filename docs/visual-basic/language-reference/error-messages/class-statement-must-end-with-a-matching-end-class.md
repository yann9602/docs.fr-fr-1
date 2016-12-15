---
title: "&#39;Class&#39; statement must end with a matching &#39;End Class&#39; | Microsoft Docs"
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
  - "vbc30481"
  - "bc30481"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30481"
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class&#39; statement must end with a matching &#39;End Class&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Class` sert à initialiser un bloc `Class` ; elle ne peut dès lors apparaître qu'au début du bloc, avec une instruction`End Class` correspondante qui termine le bloc.  Vous possédez une instruction `Class` redondante ou vous n'avez pas terminé votre bloc `Class` par `End Class`.  
  
 **ID d'erreur :** BC30481  
  
### Pour corriger cette erreur  
  
-   Recherchez et supprimez l'instruction `Class` inutile.  
  
-   Terminez le bloc `Class` par une instruction `End Class` correspondante.  
  
## Voir aussi  
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)