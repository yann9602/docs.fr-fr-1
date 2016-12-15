---
title: "Object variable or With block variable not set | Microsoft Docs"
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
  - "vbrID91"
dev_langs: 
  - "VB"
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object variable or With block variable not set
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une variable non valide est référencée.  Pour créer une variable objet, déclarez\-la, puis assignez\-lui une référence valide à l'aide de l'instruction `Set`.  De même, un bloc `With...End With` doit être initialisé en exécutant le point d'entrée de l'instruction `With`.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la variable objet référence bien un objet valide et spécifiez \(ou spécifiez de nouveau\) une référence pour l'objet.  
  
2.  Vérifiez que vous n'avez pas utilisé de variable objet avec pour valeur `Nothing`.  
  
3.  Vérifiez que la bibliothèque d'objets dans laquelle l'objet a été décrit a été sélectionnée dans la boîte de dialogue `Add References`.  
  
4.  Vérifiez que votre bloc `With` s'est initialisé en exécutant le point d'entrée de l'instruction `With`.  
  
## Voir aussi  
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)