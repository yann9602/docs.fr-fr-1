---
title: "Resume Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Resume"
  - "vb.ResumeNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Next statement, Resume"
  - "Resume Next statement"
  - "execution, resuming"
  - "run-time errors, resuming after"
  - "Resume statement, syntax"
  - "errors [Visual Basic], resuming after"
  - "Error statement, and Resume statement"
  - "execution"
  - "Resume statement"
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Resume Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Reprend l'exécution dès la fin d'une routine de gestion des erreurs.  
  
 Nous vous suggérons d'utiliser la gestion structurée des exceptions dans votre code autant que possible, plutôt que d'utiliser la gestion non structurée des exceptions et les instructions d' `On Error` et d' `Resume` .  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Syntaxe  
  
```  
Resume [ Next | line ]  
```  
  
## Composants  
 `Resume`  
 Obligatoire.  Si l'erreur s'est produite dans la même procédure que le gestionnaire d'erreurs, l'exécution reprend par l'instruction qui a engendré l'erreur.  Si l'erreur s'est produite dans une procédure appelée, l'exécution reprend par la dernière instruction qui a appelé la procédure contenant la routine de gestion des erreurs.  
  
 `Next`  
 Facultatif.  Si l'erreur s'est produite dans la même procédure que le gestionnaire d'erreurs, l'exécution reprend par l'instruction qui suit celle qui a engendré l'erreur.  Si l'erreur s'est produite dans une procédure appelée, l'exécution reprend par l'instruction qui suit celle qui a appelé la procédure contenant la routine de gestion des erreurs \(ou l'instruction `On Error Resume Next`\).  
  
 `line`  
 Facultatif.  L'exécution reprend à la ligne spécifiée dans l'argument `line` requis.  L'argument `line` est une étiquette de ligne ou un numéro de ligne et doit se trouver dans la même procédure que le gestionnaire d'erreurs.  
  
## Notes  
  
> [!NOTE]
>  Nous vous recommandons d'utiliser la gestion structurée des exceptions dans votre code autant que possible, plutôt que d'utiliser la gestion non structurée des exceptions et les instructions d' `On Error` et d' `Resume` .  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Si vous utilisez une instruction `Resume` à un autre endroit que dans la routine de gestion des erreurs, une erreur se produit.  
  
 L'instruction `Resume` ne peut pas être utilisée dans toutes les procédures qui contiennent une instruction `Try...Catch...Finally`.  
  
## Exemple  
 Cet exemple utilise l'instruction `Resume` pour terminer la gestion des erreurs dans une procédure, puis reprend l'exécution par l'instruction qui a généré l'erreur.  L'erreur numéro 55 est générée pour illustrer l'utilisation de l'instruction `Resume`.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## Configuration requise  
 **Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** bibliothèque Runtime Visual Basic \(dans Microsoft.VisualBasic.dll\)  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)