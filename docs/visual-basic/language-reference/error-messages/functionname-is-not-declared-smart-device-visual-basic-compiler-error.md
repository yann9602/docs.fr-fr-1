---
title: "&#39;&lt;functionname&gt;&#39; is not declared (Smart Device/Visual Basic Compiler Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30766"
  - "vbc30766"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30766"
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# &#39;&lt;functionname&gt;&#39; is not declared (Smart Device/Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`functionname`\> n'est pas déclaré.  La fonctionnalité d'E\/S de fichier est normalement disponible dans l'espace de noms `Microsoft.VisualBasic`, mais la version ciblée du .NET Compact Framework ne la prend pas en charge.  
  
 **ID d'erreur :** BC30766  
  
### Pour corriger cette erreur  
  
-   Effectuez des opérations sur des fichiers à l'aide de fonctions définies dans l'espace de noms `System.IO`.  
  
## Voir aussi  
 <xref:System.IO>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)