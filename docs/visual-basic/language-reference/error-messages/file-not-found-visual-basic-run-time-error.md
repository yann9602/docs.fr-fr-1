---
title: "File not found (Visual Basic Run-Time Error) | Microsoft Docs"
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
  - "vbrID53"
dev_langs: 
  - "VB"
ms.assetid: 57addb16-6f9a-444d-8af8-dda52431daca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# File not found (Visual Basic Run-Time Error)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le fichier n'a pas été trouvé à l'endroit spécifié.  Les causes de cette erreur peuvent être les suivantes :  
  
-   Une instruction fait référence à un fichier qui n'existe pas.  
  
-   Une tentative a été effectuée d'appeler une procédure dans une bibliothèque de liens dynamiques \(DLL, Dynamic\-Link Library\), mais la bibliothèque spécifiée dans la clause `Lib` de l'instruction `Declare` est introuvable.  
  
-   Vous avez tenté d'ouvrir un projet ou de charger un fichier texte qui n'existe pas.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l'orthographe du nom de fichier et la spécification du chemin d'accès.  
  
## Voir aussi  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)