---
title: "Bad file name or number | Microsoft Docs"
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
  - "vbrID52"
dev_langs: 
  - "VB"
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad file name or number
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une erreur s'est produite lors de la tentative d'accès au fichier spécifié.  Cette erreur peut se produire pour de nombreuses raisons.  
  
-   Une instruction fait référence à un fichier par un nom de fichier ou un nombre non spécifié dans l'instruction `FileOpen` ou qui a été spécifié dans une instruction `FileOpen`, mais qui a été fermé ultérieurement.  
  
-   Une instruction fait référence à un fichier par un nombre situé en dehors de la plage des nombres de fichier.  
  
-   Une instruction fait référence à un nom ou nombre de fichier qui n'est pas valide.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom de fichier est spécifié dans une instruction `FileOpen`.  Notez que si vous avez appelé l'instruction `FileClose` sans arguments, vous avez peut\-être fermé tous les fichiers ouverts par inadvertance.  
  
2.  Si votre code génère des nombres de fichier par algorithme, vérifiez que les nombres sont valides.  
  
3.  Vérifiez que les noms de fichiers sont conformes aux conventions du système d'exploitation.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)