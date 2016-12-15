---
title: "Variable uses an Automation type not supported in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID458"
dev_langs: 
  - "VB"
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable uses an Automation type not supported in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous avez essayé d'utiliser une variable définie dans une bibliothèque de types ou une bibliothèque d'objets dont le type de données n'est pas pris en charge par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Pour corriger cette erreur  
  
-   Utilisez une variable d'un type reconnue par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
     ou  
  
-   Si vous rencontrez cette erreur lors de l'utilisation de `FileGet` ou `FileGetOBject`, vérifiez que le fichier que vous essayez d'utiliser a été écrit avec `FilePut` ou `FilePutObject`.  
  
## Voir aussi  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)