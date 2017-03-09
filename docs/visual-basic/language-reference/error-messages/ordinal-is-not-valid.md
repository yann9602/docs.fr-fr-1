---
title: "Ordinal is not valid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID452"
dev_langs: 
  - "VB"
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Ordinal is not valid
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Votre appel à une bibliothèque de liens dynamiques \(DLL, Dynamic\-Link Library\) spécifie d'utiliser un nombre au lieu d'un nom de procédure, à l'aide de la syntaxe `#num`.  Les causes de cette erreur peuvent être les suivantes :  
  
-   Une tentative de convertir l'expression `#num` en un nombre a échoué.  
  
-   L'expression `#num` spécifiée n'indique pas de fonction dans la DLL.  
  
-   Une bibliothèque de types possède une déclaration non valide entraînant une utilisation interne d'un nombre ordinal non valide.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l'expression représente un nombre valide ou appelez la procédure par le nom.  
  
2.  Vérifiez que `#num` identifie une fonction valide dans la DLL.  
  
3.  Isolez l'appel de procédure générant le problème en commentant le code.  Écrivez une instruction `Declare` pour la procédure et signalez le problème au fournisseur de la bibliothèque de types.  
  
## Voir aussi  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)