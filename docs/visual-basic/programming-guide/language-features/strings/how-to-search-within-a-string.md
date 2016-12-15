---
title: "How to: Search Within a String (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], finding"
  - "strings [Visual Basic], searching"
  - "examples [Visual Basic], strings"
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Search Within a String (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cet exemple appelle la méthode <xref:System.String.IndexOf%2A> sur un objet <xref:System.String> pour rapporter l'index de la première occurrence d'une sous\-chaîne.  
  
## Exemple  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une instruction `Imports` spécifiant l'espace de noms <xref:System>.  Pour plus d'informations, consultez [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Programmation fiable  
 La méthode <xref:System.String.IndexOf%2A> rapporte l'emplacement du premier caractère de la première occurrence de la sous\-chaîne.  L'index est de base 0, ce qui signifie que l'index du premier caractère d'une chaîne est 0.  
  
 Si la méthode <xref:System.String.IndexOf%2A> ne trouve pas la sous\-chaîne, elle retourne \-1.  
  
 La méthode <xref:System.String.IndexOf%2A> respecte la casse et utilise la culture actuelle.  
  
 Pour un contrôle optimal des erreurs, vous pouvez faire figurer la recherche de chaîne dans le bloc `Try` d'une construction [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Voir aussi  
 <xref:System.String.IndexOf%2A>   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)