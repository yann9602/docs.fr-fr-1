---
title: "Comment : accéder aux caractères dans les chaînes en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Comment : accéder aux caractères dans les chaînes en Visual Basic
Cet exemple montre comment utiliser le <xref:System.String.Chars%2A> propriété pour accéder au caractère à l’emplacement spécifié dans une chaîne.  
  
## <a name="example"></a>Exemple  
 Il est parfois utile de disposer de données sur les caractères de votre chaîne ainsi que les positions de ces caractères dans la chaîne. Vous pouvez considérer une chaîne sous forme de tableau de caractères (`Char` instances) ; vous pouvez récupérer un caractère particulier en faisant référence à l’index de ce caractère via la <xref:System.String.Chars%2A> propriété.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 Le `index` paramètre de la <xref:System.String.Chars%2A> propriété est de base zéro.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le <xref:System.String.Chars%2A> propriété retourne le caractère situé à la position spécifiée. Toutefois, certains caractères Unicode peuvent être représentés par plusieurs caractères. Pour plus d’informations sur l’utilisation des caractères Unicode, consultez [Comment : convertir une chaîne en un tableau de caractères](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 Le <xref:System.String.Chars%2A> propriété lève une <xref:System.IndexOutOfRangeException> exception si le `index` paramètre est supérieur ou égal à la longueur de la chaîne, ou si elle est inférieure à zéro  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String.Chars%2A>  
 [Guide pratique : convertir une chaîne en tableau de caractères](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Conversion entre chaînes et d’autres types de données en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)
