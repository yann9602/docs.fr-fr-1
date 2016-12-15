---
title: "Impossible d’appliquer &#224; la fois &#39;System.STAThreadAttribute&#39; et &#39;System.MTAThreadAttribute&#39; &#224; &#39;|1&#39; | Microsoft Docs"
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
  - "bc31513"
  - "vbc31513"
helpviewer_keywords: 
  - "BC31513"
ms.assetid: 7efb4c8e-d31c-4273-9d85-8cd2bef4d120
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer &#224; la fois &#39;System.STAThreadAttribute&#39; et &#39;System.MTAThreadAttribute&#39; &#224; &#39;|1&#39;
Les attributs `System.STAThreadAttribute` et `System.MTAThreadAttribute` s’excluent mutuellement.  
  
 **ID d’erreur :** BC31513  
  
### Pour corriger cette erreur  
  
1.  Appliquez `System.MTAThreadAttribute` ou `System.STAThreadAttribute`, mais pas les deux.  
  
## Voir aussi  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)