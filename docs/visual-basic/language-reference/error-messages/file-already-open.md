---
title: "File already open | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID55"
dev_langs: 
  - "VB"
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# File already open
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un fichier doit parfois être fermé avant qu'une opération `FileOpen` ou qu'une autre opération ne se produise.  Cette erreur peut se produire pour de nombreuses raisons.  
  
-   Une opération `FileOpen` de mode séquentiel Output a été exécutée pour un fichier déjà ouvert.  
  
-   Une instruction fait référence à un fichier ouvert.  
  
### Pour corriger cette erreur  
  
1.  Fermez le fichier avant d'exécuter l'instruction.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>