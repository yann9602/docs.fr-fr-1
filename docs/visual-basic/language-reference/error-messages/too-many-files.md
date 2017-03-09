---
title: "Too many files | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID67"
dev_langs: 
  - "VB"
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Too many files
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Plus de fichiers que ceux qui sont autorisés par le système d'exploitation ont été créés dans le répertoire racine ou plus de fichiers que le nombre spécifié dans le paramètre **files\=** de votre fichier CONFIG.SYS ont été ouverts.  
  
### Pour corriger cette erreur  
  
1.  Si votre programme ouvre, ferme ou enregistre des fichiers dans le répertoire racine, modifiez votre programme afin qu'il utilise un sous\-répertoire.  
  
2.  Augmentez le nombre de fichiers spécifié dans le paramètre **files\=** de votre fichier CONFIG.SYS et redémarrez votre ordinateur.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)