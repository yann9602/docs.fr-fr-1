---
title: "Continue Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.continue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Continue statement [Visual Basic]"
  - "loops, transferring to next iteration"
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Continue Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Transfère immédiatement le contrôle vers l'itération suivante d'une boucle.  
  
## Syntaxe  
  
```  
Continue { Do | For | While }  
```  
  
## Notes  
 Vous pouvez effectuer un transfert de l'intérieur d'une boucle `Do`, `For` ou `While` vers l'itération suivante de cette même boucle.  Le contrôle passe immédiatement au test de condition de la boucle, qui équivaut à effectuer un transfert vers l'instruction `For` ou `While` ou vers l'instruction `Do` ou `Loop` qui contient la clause `Until` ou `While`.  
  
 Vous pouvez utiliser `Continue` à n'importe quel emplacement de la boucle qui autorise les transferts.  Les règles qui autorisent le transfert de contrôle sont identiques à celles de l'[GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Par exemple, si une boucle est entièrement contenue dans un bloc `Try`, un bloc `Catch` ou un bloc `Finally`, vous pouvez utiliser `Continue` pour effectuer un transfert hors de la boucle.  En revanche, si la structure `Try`...`End Try` est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle hors du bloc `Finally`, et vous pouvez l'utiliser pour le transférer hors d'un bloc `Try` ou `Catch` uniquement si le transfert s'effectue entièrement hors de la structure `Try`...`End Try`.  
  
 Si vous disposez de boucles imbriquées du même type, par exemple, une boucle `Do` dans une autre boucle `Do`, une instruction `Continue Do` passe à l'itération suivante de la boucle `Do` la plus profonde qui la contient.  Vous ne pouvez pas utiliser `Continue` pour passer à l'itération suivante d'une boucle conteneur du même type.  
  
 Si vous disposez de boucles imbriquées de types différents, par exemple une boucle `Do` dans une boucle `For`, vous pouvez passer à l'itération suivante de l'une ou l'autre des boucles à l'aide de `Continue Do` ou `Continue For`.  
  
## Exemple  
 L'exemple de code suivant utilise l'instruction `Continue While` pour passer à la colonne suivante d'un tableau si un diviseur est nul.  L'instruction `Continue While` est à l'intérieur d'une boucle `For`.  Elle effectue un transfert vers l'instruction `While col < lastcol`, qui est l'itération suivante de la boucle `While` la plus profonde qui contient la boucle `For`.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## Voir aussi  
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)