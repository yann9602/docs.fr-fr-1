---
title: "Permission denied (Visual Basic) | Microsoft Docs"
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
  - "vbrID70"
dev_langs: 
  - "VB"
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Permission denied (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une tentative d'écriture sur un disque protégé en écriture ou d'accès à un fichier verrouillé a été effectuée.  
  
### Pour corriger cette erreur  
  
1.  Pour ouvrir un fichier protégé en écriture, modifiez l'attribut de protection en écriture du fichier.  
  
2.  Assurez\-vous qu'aucun autre processus n'a verrouillé le fichier et attendez avant d'ouvrir le fichier que l'autre processus le libère.  
  
3.  Pour accéder au Registre, vérifiez que vos autorisations d'utilisateur incluent bien ce type d'accès au Registre.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)