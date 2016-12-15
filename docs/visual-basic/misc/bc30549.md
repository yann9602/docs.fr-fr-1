---
title: "L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; un module | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30549"
  - "bc30549"
helpviewer_keywords: 
  - "BC30549"
ms.assetid: b38fea31-6b0b-4c54-9518-b59226505802
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; un module
Vous avez tenté d’appliquer un attribut à un module dont le `AttributeUsageAttribute` ne spécifie pas `AttributeTargets.Module`. Lorsque l’attribut a été déclaré, il n’a pas été défini pour être appliqué à un module.  
  
 **ID d’erreur :** BC30549  
  
### Pour corriger cette erreur  
  
1.  Vérifiez la déclaration d’attribut et spécifiez `AttributeTargets.Module`ou`AttributeTargets.All`.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>