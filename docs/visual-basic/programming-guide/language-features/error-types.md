---
title: "Error Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, types"
  - "errors [Visual Basic], types"
  - "errors [Visual Basic], logic"
  - "errors [Visual Basic], syntax"
  - "logic errors, Visual Basic"
  - "run-time errors, types of errors"
  - "syntax errors, Visual Basic"
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], les erreurs \(également appelées *exceptions*\) sont classées dans l'une des trois catégories suivantes : erreurs de syntaxe, erreurs d'exécution et erreurs de logique.  
  
## Erreurs de syntaxe  
 Les *erreurs de syntaxe* apparaissent lors de l'écriture du code.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vérifie votre code au fur et à mesure que vous le tapez dans la fenêtre **Éditeur de code** et vous signale vos erreurs telles qu'un mot mal orthographié ou l'utilisation incorrecte d'un élément de langage.  Les erreurs de syntaxe représentent le type d'erreur le plus fréquent.  Vous pouvez les résoudre facilement dans l'environnement de codage dès qu'elles se produisent.  
  
> [!NOTE]
>  L'instruction `Option Explicit` permet d'éviter des erreurs de syntaxe.  Elle vous force à déclarer à l'avance toutes les variables qui doivent être utilisées dans l'application.  Par conséquent, lorsque ces variables sont utilisées dans le code, les erreurs typographiques sont décelées immédiatement et peuvent être résolues.  
  
## Erreurs d'exécution  
 Les *erreurs d'exécution* sont celles qui apparaissent uniquement après la compilation et l'exécution de votre code.  Elles sont liées à un code qui semble correct parce qu'il ne présente pas d'erreurs de syntaxe, mais dont l'exécution est impossible.  Par exemple, vous pouvez écrire correctement une ligne de code permettant d'ouvrir un fichier.  Mais si le fichier est endommagé, l'application ne peut pas exécuter la fonction `Open`, et son exécution est interrompue.  Vous pouvez résoudre la plupart des erreurs d'exécution en réécrivant le code erroné, en le recompilant et en le ré\-exécutant.  
  
## Erreurs de logique  
 Les *erreurs de logique* sont celles qui apparaissent lorsque l'application est en cours d'utilisation.  Elles correspondent le plus souvent à des résultats non souhaités ou inattendus en réponse à des actions de l'utilisateur.  Par exemple, le fait d'appuyer sur une mauvaise touche ou une influence extérieure peuvent entraîner l'arrêt de votre application dans les paramètres prévus ou de manière complète.  Les erreurs de logique sont les plus difficiles à résoudre, car il n'est pas toujours facile de déterminer leur origine.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Principes de base du débogueur](/visual-studio/debugger/debugger-basics)