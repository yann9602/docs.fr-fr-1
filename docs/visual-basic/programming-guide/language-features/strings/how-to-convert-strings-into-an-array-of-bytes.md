---
title: "How to: Convert Strings into an Array of Bytes in Visual Basic | Microsoft Docs"
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
  - "string conversion, arrays"
  - "arrays [Visual Basic], converting strings to"
  - "byte arrays"
  - "examples [Visual Basic], string conversion"
  - "arrays [Visual Basic], byte arrays"
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Convert Strings into an Array of Bytes in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette rubrique montre comment convertir une chaîne en un tableau d'octets.  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Text.Encoding.GetBytes%2A> de la classe d'encodage <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> pour convertir une chaîne en un tableau d'octets.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Vous pouvez choisir entre plusieurs options d'encodage pour convertir une chaîne en un tableau d'octets :  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName> : obtient un encodage pour le jeu de caractères ASCII \(7 bits\).  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName> : obtient un encodage pour le format UTF\-16 qui utilise l'ordre d'octet avec primauté des octets de poids fort \(Big\-endian\).  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=fullName> : obtient un encodage pour la page de codes ANSI actuelle du système.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> : obtient un encodage pour le format UTF\-16 qui utilise l'ordre d'octet avec primauté des octets de poids faible \(Big\-endian\).  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName> : obtient un encodage pour le format UTF\-32 qui utilise l'ordre d'octet avec primauté des octets de poids faible \(Big\-endian\).  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName> : obtient un encodage pour le format UTF\-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName> : obtient un encodage pour le format UTF\-8.  
  
## Voir aussi  
 <xref:System.Text.Encoding?displayProperty=fullName>   
 <xref:System.Text.Encoding.GetBytes%2A>   
 [How to: Convert an Array of Bytes into a String in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)