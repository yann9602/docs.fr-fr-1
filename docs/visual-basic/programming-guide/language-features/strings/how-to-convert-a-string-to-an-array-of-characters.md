---
title: "How to: Convert a String to an Array of Characters in Visual Basic | Microsoft Docs"
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
  - "character arrays, converting strings"
  - "arrays [Visual Basic], converting strings to"
  - "examples [Visual Basic], string conversion"
  - "strings [Visual Basic], converting to arrays"
  - "string conversion [Visual Basic], arrays"
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Convert a String to an Array of Characters in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Il est parfois utile de posséder des données sur les caractères de votre chaîne ainsi que sur les positions de ces caractères dans la chaîne, lorsque vous analysez une chaîne, par exemple.  Cet exemple montre comment vous pouvez obtenir un tableau des caractères d'une chaîne en appelant la méthode <xref:System.String.ToCharArray%2A> de la chaîne.  
  
## Exemple  
 Cet exemple montre comment fractionner une chaîne en tableau `Char`, et comment fractionner une chaîne en tableau `String` de ses caractères de texte Unicode.  Cette distinction s'explique par le fait que les caractères de texte Unicode peuvent être composés d'au moins deux caractères `Char` \(par exemple, une paire de substitution ou une séquence de caractères d'association\).  Pour plus d'informations, consultez <xref:System.Globalization.TextElementEnumerator> et « The Unicode Standard » à l'adresse http:\/\/www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## Exemple  
 Il est plus difficile de fractionner une chaîne en ses caractères de texte Unicode, mais cette procédure est nécessaire si vous avez besoin d'informations sur la représentation visuelle d'une chaîne.  Cet exemple utilise la méthode <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> pour obtenir des informations sur les caractères de texte Unicode qui composent une chaîne.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## Voir aussi  
 <xref:System.String.Chars%2A>   
 <xref:System.Globalization.StringInfo?displayProperty=fullName>   
 [How to: Access Characters in Strings](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)   
 [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)