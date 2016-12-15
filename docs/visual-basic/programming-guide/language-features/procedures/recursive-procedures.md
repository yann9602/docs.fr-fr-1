---
title: "Recursive Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, procedures"
  - "procedures, that call themselves"
  - "procedures, recursive"
  - "procedures, calling"
  - "recursive procedures"
  - "functions [Visual Basic], calling recursively"
  - "recursion"
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Recursive Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une procédure *récursive* est une procédure qui s'appelle elle\-même.  En général, ce n'est pas le moyen le plus efficace d'écrire du code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 La procédure suivante utilise la récurrence pour calculer la factorielle de son argument d'origine.  
  
 [!code-vb[VbVbcnProcedures#51](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## Considérations sur les procédures récursives  
 **Conditions de limitation** Vous devez concevoir une procédure récursive à tester pour au moins une condition qui peut mettre fin à la récurrence, et vous devez également gérer les situations pour lesquelles aucune de ces conditions n'est satisfaite pour un nombre raisonnable d'appels récursifs.  Si aucune condition ne peut être satisfaite sans erreur, votre procédure s'expose à un risque élevé d'exécution dans une boucle infinie.  
  
 **Utilisation de la mémoire**.  Votre application dispose d'un espace limité pour les variables locales.  Chaque fois qu'une procédure s'appelle elle\-même, elle utilise davantage d'espace pour les copies supplémentaires de ses variables locales.  Si le processus se poursuit indéfiniment, il peut se produire une erreur <xref:System.StackOverflowException>.  
  
 **Efficacité**.  Vous pouvez presque toujours remplacer la récurrence par une boucle.  Une boucle ne possède pas la charge mémoire pour passer des arguments, initialiser le stockage supplémentaire et retourner des valeurs.  Votre performance peut être considérablement améliorée sans appels récurrents.  
  
 **Récurrence mutuelle** Vous pouvez observer une performance médiocre ou même une boucle infinie si deux procédures s'appellent l'une et l'autre.  Ce type de conception présente les mêmes problèmes qu'une procédure récursive simple, mais peut être plus difficile à détecter et à déboguer.  
  
 **Appel avec parenthèses**.  Lorsqu'une procédure `Function` s'appelle de manière récursive, le nom de cette procédure doit être suivi de parenthèses, même s'il n'y a pas de liste d'arguments.  Sinon, le nom de la fonction est considéré comme sa valeur de retour.  
  
 **Test** Si vous écrivez une procédure récursive, vous devez la tester soigneusement afin de vous assurer qu'elle satisfait toujours certaines conditions de limitation.  Vous devez également veiller à toujours disposer d'une mémoire suffisante en dépit du grand nombre d'appels récurrents.  
  
## Voir aussi  
 <xref:System.StackOverflowException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Dépannage des exceptions : System.StackOverflowException](../Topic/Troubleshooting%20Exceptions:%20System.StackOverflowException.md)