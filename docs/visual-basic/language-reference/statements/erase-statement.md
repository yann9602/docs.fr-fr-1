---
title: "Erase Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Erase"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Erase keyword"
  - "Erase statement"
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Erase Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Utilisée pour libérer les variables tableau et la mémoire utilisée pour leurs éléments.  
  
## Syntaxe  
  
```  
Erase arraylist  
```  
  
## Composants  
 `arraylist`  
 Obligatoire.  Liste de variables tableau à effacer.  Les variables multiples sont séparées par des virgules.  
  
## Notes  
 L'instruction `Erase` peut apparaître seulement au niveau de la procédure.  En d'autres termes, vous pouvez libérer des tableaux à l'intérieur d'une procédure mais pas au niveau de la classe ou du module.  
  
 L'instruction `Erase` équivaut à assigner `Nothing` à chaque variable tableau.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Erase` pour effacer deux tableaux et libérer leur mémoire \(respectivement 1 000 et 100 éléments de stockage\).  L'instruction `ReDim` assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## Voir aussi  
 [Nothing](../../../visual-basic/language-reference/nothing.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)