---
title: "&#39;Optional&#39; expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30202"
  - "vbc30202"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30202"
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Optional&#39; expected
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un argument facultatif dans une déclaration de procédure est suivi d'un argument requis.  Tous les arguments qui suivent un argument facultatif doivent également être facultatifs.  
  
 **ID d'erreur :** BC30202  
  
### Pour corriger cette erreur  
  
1.  Si l'argument doit être requis, déplacez\-le afin qu'il précède le premier argument facultatif de la liste des arguments.  
  
2.  Si l'argument doit être facultatif, utilisez le mot clé `Optional`.  
  
## Voir aussi  
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)