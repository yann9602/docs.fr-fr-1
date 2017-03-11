---
title: "L’op&#233;rande &#39;ReDim&#39; ne peut pas &#234;tre Nothing | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# L’op&#233;rande &#39;ReDim&#39; ne peut pas &#234;tre Nothing
Une instruction `ReDim` tente d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension, mais elle ne fournit pas de valeur valide pour son opérande.  
  
### Pour corriger cette erreur  
  
-   Remplacez l’opérande `Preserve` par une valeur valide.  
  
## Voir aussi  
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD Tableaux multidimensionnels en Visual Basic](http://msdn.microsoft.com/fr-fr/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](../../visual-basic/language-reference/statements/redim-statement.md)   
 [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Preserve \- delete](http://msdn.microsoft.com/fr-fr/91badeab-b4e0-48b6-92c9-9f0c8f995d81)