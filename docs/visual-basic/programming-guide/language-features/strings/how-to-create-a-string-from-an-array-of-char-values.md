---
title: "How to: Create a String from An Array of Char Values (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "examples [Visual Basic], arrays"
  - "examples [Visual Basic], Char data type"
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# How to: Create a String from An Array of Char Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cet exemple crée la chaîne "abcd" en utilisant des caractères isolés.  
  
## Exemple  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## Compilation du code  
 Cette méthode n'a aucune exigence particulière.  
  
 La syntaxe `"a"c`, où un seul `c` suit un caractère unique entre guillemets, est utilisé pour créer un littéral de caractère.  
  
## Programmation fiable  
 Les caractères Null \(`Chr(0)`\) faisant partie de la chaîne produisent des résultats inattendus lors de l'utilisation de la chaîne.  Le caractère Null sera inclus dans la chaîne, mais dans certains cas les caractères suivants ne seront pas affichés.  
  
## Voir aussi  
 <xref:System.String>   
 [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)