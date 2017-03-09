---
title: "&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30830"
  - "vbc30830"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30830"
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les instructions Line ne sont plus prises en charge.  Les fonctionnalités d'E\/S sur fichier sont disponibles en tant que `Microsoft.VisualBasic.FileSystem.LineInput` et les fonctionnalités graphiques en tant que `System.Drawing.Graphics.DrawLine`.  
  
 **ID d'erreur :** BC30830  
  
### Pour corriger cette erreur  
  
1.  Pour accéder au fichier, utilisez `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Pour exécuter des graphiques, utilisez `System.Drawing.Graphics.Drawline`.  
  
## Voir aussi  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)