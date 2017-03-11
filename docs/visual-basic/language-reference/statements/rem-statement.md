---
title: "REM Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.'"
  - "vb.Rem"
  - "Rem"
  - "'"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "REM statement"
  - "comments, Visual Basic code"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# REM Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Utilisée pour inclure des notes explicatives dans le code source d'un programme.  
  
## Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## Composants  
 `comment`  
 Facultatif.  Texte du commentaire de votre choix que vous voulez inclure.  Un espace est requis entre les `REM` mot\-clé et `comment`.  
  
## Notes  
 Vous pouvez mettre une instruction `REM` toute seule sur une ligne ou bien vous pouvez la mettre sur une ligne qui suit une autre instruction.  L'instruction `REM` doit être la dernière instruction de la ligne.  Si elle suit une autre instruction, `REM` doit être séparée de cette instruction par un espace.  
  
 Vous pouvez utiliser un guillemet simple \(`'`\) à la place de `REM`.  Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou s'il se trouve tout seul sur une ligne.  
  
> [!NOTE]
>  Vous ne pouvez pas continuer une instruction `REM` à l'aide d'une séquence de continuation de ligne \(`_`\).  Une fois le commentaire commencé, le compilateur n'examine plus les caractères pour y rechercher une signification particulière.  Lorsqu'un commentaire tient sur plusieurs lignes, utilisez une autre instruction `REM` ou un symbole de commentaire \(`'`\) sur chaque ligne.  
  
## Exemple  
 L'exemple suivant illustre l'instruction `REM` qui est utilisée pour inclure des notes explicatives dans un programme.  Il montre également qu'il est possible d'utiliser le guillemet simple \(`'`\) à la place de `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/rem-statement_1.vb)]  
  
## Voir aussi  
 [Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)   
 [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)