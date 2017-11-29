---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06e5c6923c26f3cb84b38475d6680523853d727d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)
Cet exemple crée la chaîne « abcd » à partir de différents caractères.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cette méthode n’a pas d’exigences particulières.  
  
 La syntaxe `"a"c`, où un seul `c` suit un caractère unique entre guillemets, est utilisé pour créer un caractère littéral.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les caractères null (équivalent à `Chr(0)`) dans la chaîne de produire des résultats inattendus lors de l’utilisation de la chaîne. Le caractère null sera inclus dans la chaîne, mais pas les caractères suivant le caractère null seront affichera dans certaines situations.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String>  
 [Char (type de données)](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
