---
title: "Zero-based vs. One-based String Access in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], indexing"
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Zero-based vs. One-based String Access in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique compare la façon dont [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] et [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] permettent d'accéder aux caractères dans une chaîne.  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] fournit toujours un accès de base zéro aux caractères d'une chaîne, alors que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit un accès de base zéro et de base un, selon la fonction.  
  
## Base 1  
 Pour obtenir un exemple de fonction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] de base 1, prenez la fonction `Mid`.  Elle prend un argument qui indique la position de caractère à laquelle la sous\-chaîne commencera, en démarrant à la position 1.  La méthode <xref:System.String.Substring%2A?displayProperty=fullName> de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] prend un index du caractère de la chaîne où la sous\-chaîne doit démarrer, en commençant à la position 0.  Ainsi, pour une chaîne "ABCDE", les différents caractères sont numérotés 1,2,3,4,5 pour la fonction `Mid`, mais 0,1,2,3,4 pour la méthode <xref:System.String.Substring%2A?displayProperty=fullName>.  
  
## Base zéro  
 Pour obtenir un exemple d'une fonction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] de base zéro, prenez la fonction `Split`.  Elle fractionne une chaîne et retourne un tableau contenant les sous\-chaînes.  La méthode <xref:System.String.Split%2A?displayProperty=fullName> de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] fractionne également une chaîne et retourne un tableau contenant les sous\-chaînes.  Dans la mesure où la fonction `Split` et la méthode <xref:System.String.Split%2A> retournent des tableaux [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)], elles doivent être de base zéro.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)