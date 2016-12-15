---
title: "Sub or Function not defined (Visual Basic) | Microsoft Docs"
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
  - "vbrID35"
dev_langs: 
  - "VB"
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub or Function not defined (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un `Sub` ou un `Function` doit être défini afin d'être appelé.  Cette erreur peut avoir plusieurs causes :  
  
-   Faute d'orthographe dans le nom de la procédure.  
  
-   Tentative d'appeler une procédure à partir d'un autre projet sans ajouter explicitement de référence à ce projet dans la boîte de dialogue **Références**.  
  
-   Spécification d'une procédure qui n'est pas visible pour la procédure appelante.  
  
-   Déclaration d'une routine de bibliothèque de liens dynamiques \(DLL, Dynamic\-Link Library\) Windows ou d'une routine de ressource de code Macintosh qui ne se trouve pas dans la bibliothèque spécifiée ou dans la ressource de code.  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que le nom de la procédure est correctement orthographié.  
  
2.  Recherchez le nom du projet contenant la procédure que vous voulez appeler dans la boîte de dialogue **Références**.  Si celui\-ci n'apparaît pas, cliquez sur le bouton **Parcourir** pour le rechercher.  Activez la case à cocher située à gauche du nom de projet, puis cliquez sur **OK**.  
  
3.  Vérifiez le nom de la routine.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)