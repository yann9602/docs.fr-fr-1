---
title: "L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; un assembly | Microsoft Docs"
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
  - "bc30548"
  - "vbc30548"
helpviewer_keywords: 
  - "BC30548"
ms.assetid: bc36f094-626a-4907-b80b-f195155fa5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; un assembly
Vous avez tenté d’appliquer un attribut à un assembly dont `AttributeUsageAttribute` ne spécifie pas `AttributeTargets.Assembly`. Quand l’attribut a été déclaré, il n’a pas été défini pour être appliqué à un assembly.  
  
 **ID d’erreur :** BC30548  
  
### Pour corriger cette erreur  
  
1.  Vérifiez la déclaration d’attribut et spécifiez `AttributeTargets.Assembly` ou `AttributeTargets.All`.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>