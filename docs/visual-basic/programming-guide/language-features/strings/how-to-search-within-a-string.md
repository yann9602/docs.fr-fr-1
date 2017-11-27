---
title: "Comment : effectuer une recherche dans une chaîne (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Comment : effectuer une recherche dans une chaîne (Visual Basic)
Cet exemple appelle la <xref:System.String.IndexOf%2A> méthode sur un <xref:System.String> objet à l’index de la première occurrence d’une sous-chaîne de rapports.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Un `Imports` instruction en spécifiant le <xref:System> espace de noms. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le <xref:System.String.IndexOf%2A> méthode signale l’emplacement du premier caractère de la première occurrence de la sous-chaîne. L’index est basé sur 0, ce qui signifie que le premier caractère d’une chaîne est un index de 0.  
  
 Si <xref:System.String.IndexOf%2A> ne trouve pas la sous-chaîne, elle retourne -1.  
  
 Le <xref:System.String.IndexOf%2A> méthode respecte la casse et utilise la culture actuelle.  
  
 Pour un contrôle optimal des erreurs, vous pouvez souhaiter placez la recherche de chaîne dans le `Try` bloquer d’un [essayez... Catch... Instruction finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String.IndexOf%2A>  
 [Try...Catch...Finally (instruction)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Chaînes](../../../../visual-basic/programming-guide/language-features/strings/index.md)
