---
title: "Expression does not produce a value | Microsoft Docs"
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
  - "vbc30491"
  - "bc30491"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30491"
ms.assetid: 8399d7ae-bc0a-49e6-81dc-2e7229708bc9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression does not produce a value
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous avez tenté d'utiliser une expression qui ne produit aucune valeur dans un contexte produisant des valeurs, tel que l'appel d'une instruction `Sub` dans un contexte où une fonction `Function` est attendue.  
  
 **ID d'erreur :** BC30491  
  
### Pour corriger cette erreur  
  
-   Remplacez l'expression par une expression produisant une valeur.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)