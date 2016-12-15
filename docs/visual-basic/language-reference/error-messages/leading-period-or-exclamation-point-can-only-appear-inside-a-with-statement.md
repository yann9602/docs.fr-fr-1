---
title: "Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement | Microsoft Docs"
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
  - "vbc30157"
  - "bc30157"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30157"
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un point \(.\) ou un point d'exclamation \(\!\) qui ne se trouve pas à l'intérieur d'un bloc `With` apparaît sans expression à gauche.  L'accès au membre \(`.`\) et l'accès au membre dictionnaire \(`!`\) requièrent une expression spécifiant l'élément contenant le membre.  Celui\-ci doit apparaître immédiatement à gauche de l'accesseur ou comme cible d'un bloc `With` contenant l'accès au membre.  
  
 **ID d'erreur :** BC30157  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le bloc `With` est correctement mis en forme.  
  
2.  En l'absence de bloc `With`, ajoutez une expression à gauche de l'accesseur qui correspond à un élément défini contenant le membre.  
  
## Voir aussi  
 [Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)