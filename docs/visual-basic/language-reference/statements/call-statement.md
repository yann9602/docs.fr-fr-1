---
title: "Call Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Call"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, Call statement"
  - "Call statement"
  - "procedures, calling"
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Call Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Transfère le contrôle à une procédure `Function`, `Sub` ou à une procédure de bibliothèque de liens dynamiques \(DLL, Dynamic\-Link Library\).  
  
## Syntaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## Composants  
 `procedureName`  
 Obligatoire.  Nom de la procédure à appeler.  
  
 `argumentList`  
 Facultatif.  Liste de variables ou d'expressions représentant les arguments passés à la procédure quand elle est appelée.  Les arguments multiples sont séparés par des virgules.  Si vous incorporez `argumentList`, vous devez le placer entre parenthèses.  
  
## Notes  
 Vous pouvez utiliser le mot clé d' `Call` lorsque vous appelez une procédure.  Pour la plupart des appels de procédure, vous n'êtes pas obligé d'utiliser ce mot clé.  
  
 Vous utilisez généralement le mot clé d' `Call` lorsque l'expression appelée ne commence pas par un identificateur.  L'utilisation du mot clé d' `Call` pour d'autres utilisations n'est pas recommandée.  
  
 Si la procédure retourne une valeur, l'instruction `Call` l'ignore.  
  
## Exemple  
 Le code suivant présente deux situations où le mot clé d' `Call` est nécessaire pour appeler une procédure.  Dans les deux exemples, l'expression appelée ne commence pas par un identificateur.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## Voir aussi  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)