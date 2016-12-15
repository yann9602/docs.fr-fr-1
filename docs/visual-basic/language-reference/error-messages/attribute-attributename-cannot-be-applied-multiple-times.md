---
title: "Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times | Microsoft Docs"
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
  - "bc30663"
  - "vbc30663"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30663"
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'attribut ne peut être appliqué qu'une seule fois.  L'attribut `AttributeUsage` détermine si un attribut peut être appliqué plusieurs fois.  
  
 **ID d'erreur :** BC30663  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l'attribut n'est appliqué qu'une seule fois.  
  
2.  Si vous utilisez des attributs personnalisés que vous avez développés, modifiez l'attribut `AttributeUsage` de manière à ce qu'il autorise l'utilisation de plusieurs attributs, comme dans l'exemple suivant.  
  
    ```  
    <AttributeUsage(AllowMultiple := True)>  
    ```  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [Création d'attributs personnalisés](../Topic/Creating%20Custom%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [AttributeUsage](../Topic/AttributeUsage%20\(C%23%20and%20Visual%20Basic\).md)