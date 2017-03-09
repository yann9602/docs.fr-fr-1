---
title: "Function evaluation is disabled because a previous function evaluation timed out | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30957"
  - "vbc30957"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30957"
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Function evaluation is disabled because a previous function evaluation timed out
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'évaluation de la fonction est désactivée, car une évaluation de fonction précédente a expiré.Pour réactiver l'évaluation de la fonction, effectuez à nouveau le pas à pas détaillé ou relancez le débogage.  
  
 Dans le débogueur Visual Studio, une expression spécifie un appel de procédure, mais une autre évaluation a expiré.  
  
 Les causes possibles de l'expiration d'un appel de procédure sont, entre autres, une boucle infinie ou une *boucle sans fin*.  Pour plus d'informations, consultez [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Un cas particulier d'une boucle infinie est la *récursivité*.  Pour plus d'informations, consultez [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID d'erreur :** BC30957  
  
### Pour corriger cette erreur  
  
1.  Si possible, déterminez la précédente évaluation de fonction et la cause de son expiration.  Sinon, cette erreur risque de se reproduire.  
  
2.  Exécutez à nouveau le débogueur pas à pas, ou arrêtez et relancez le débogage.  
  
## Voir aussi  
 [Débogage dans Visual Studio](/visual-studio/debugger/debugging-in-visual-studio)   
 [Naviguer dans le code avec le débogueur](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [Expressions dans Visual Basic](../Topic/Expressions%20in%20Visual%20Basic.md)