---
title: "Automation error | Microsoft Docs"
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
  - "vbrID440"
dev_langs: 
  - "VB"
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Automation error
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention \/ la définition d'une propriété de variable objet. L'application qui a créé l'objet a signalé l'erreur.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.  
  
2.  Utilisez  l'instruction `On Error Resume Next` immédiatement avant l'instruction d'accès, puis vérifiez les erreurs immédiatement après l'instruction d'accès.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Nous contacter](/visual-studio/ide/talk-to-us)