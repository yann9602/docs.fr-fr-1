---
title: "Alias Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Alias"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Alias keyword"
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Alias Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Indique qu'une procédure externe possède un autre nom dans sa DLL.  
  
## Notes  
 Le mot clé `Alias` peut être utilisé dans le contexte suivant :  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 Dans l'exemple suivant, le mot clé `Alias` est utilisé pour fournir le nom de la fonction dans advapi32.dll, `GetUserNameA`, ce `getUserName` est utilisé à sa place dans cet exemple.  La fonction `getUserName` est appelée dans la sous\-fonction `getUser`, qui affiche le nom de l'utilisateur actuel.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/alias-clause_1.vb)]  
  
## Voir aussi  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)