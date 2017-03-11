---
title: "Bad DLL calling convention | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID49"
dev_langs: 
  - "VB"
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Bad DLL calling convention
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les arguments passés à une bibliothèque de liens dynamiques \(DLL, Dynamic\-Link Library\) doivent correspondre exactement à ceux qui sont attendus par la routine.  L'appel de conventions traite des nombres, types et ordres des arguments.  Votre programme peut appeler une routine dans une DLL à laquelle est passé un type ou un nombre incorrect d'arguments.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que tous les types d'argument correspondent à ceux spécifiés dans la déclaration de la routine que vous appelez.  
  
2.  Vérifiez que vous passez le même nombre d'arguments que celui qui est indiqué dans la déclaration de la routine que vous appelez.  
  
3.  Si la routine DLL attend des arguments par valeur, vérifiez que `ByVal` est spécifié pour ces arguments dans la déclaration de la routine.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)