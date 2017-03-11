---
title: "Stop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Stop"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "breakpoints, Stop statements"
  - "Stop statements, syntax"
  - "Stop statements"
  - "execution, suspending"
  - "processing, interrupting"
  - "processes, interrupting"
  - "execution, stopping"
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Stop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Interrompt l'exécution.  
  
## Syntaxe  
  
```  
Stop  
```  
  
## Notes  
 Vous pouvez placer des instructions `Stop` n'importe où dans les procédures afin d'en interrompre l'exécution.  Utiliser l'instruction `Stop` revient à placer un point d'arrêt dans le code.  
  
 L'instruction `Stop` interrompt l'exécution, mais contrairement à `End`, elle ne ferme pas les fichiers et n'efface pas les variables, sauf si elle est placée dans un fichier exécutable \(.exe\) compilé.  
  
> [!NOTE]
>  Si l'instruction `Stop` figure dans le code qui s'exécute en dehors de l'environnement de développement intégré \(IDE, Integrated Development Environment\), le débogueur est appelé.  C'est le cas quel que soit le mode de compilation du code \(mode débogage ou mode commercial\).  
  
## Exemple  
 Cet exemple utilise l'instruction `Stop` pour suspendre l'exécution à chaque itération de la boucle `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/stop-statement_1.vb)]  
  
## Voir aussi  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)