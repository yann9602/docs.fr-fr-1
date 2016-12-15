---
title: "Input past end of file | Microsoft Docs"
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
  - "vbrID62"
dev_langs: 
  - "VB"
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Input past end of file
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction `Input` lit à partir d'un fichier vide ou d'un fichier dans lequel toutes les données sont utilisées ou vous avez utilisé la fonction `EOF` avec un fichier ouvert pour un accès binaire.  
  
### Pour corriger cette erreur  
  
1.  Utilisez la fonction `EOF` immédiatement avant l'instruction `Input` pour détecter la fin du fichier.  
  
2.  Si le fichier est ouvert pour un accès binaire, utilisez `Seek` et `Loc`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>