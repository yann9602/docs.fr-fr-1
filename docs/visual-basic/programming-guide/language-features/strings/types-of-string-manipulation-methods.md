---
title: "Types of String Manipulation Methods in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "strings [Visual Basic], manipulating [Visual Basic]"
  - "string manipulation"
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Types of String Manipulation Methods in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Il existe plusieurs méthodes différentes pour analyser et manipuler vos chaînes.  Certaines de ces méthodes font partie du langage [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], tandis que d'autres sont inhérentes à la classe `String`.  
  
## Langage Visual Basic et le .NET Framework  
 Les méthodes [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sont utilisées en tant que fonctions inhérentes du langage.  Elles peuvent être utilisées sans qualification dans votre code.  L'exemple suivant illustre une utilisation classique d'une commande [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de manipulation de chaîne :  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Dans cet exemple, la fonction `Mid` effectue une opération directe sur `aString` et assigne la valeur à `bString`.  
  
 Pour une liste des méthodes Visual Basic de manipulation de chaîne, consultez [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### Méthodes partagées et méthodes d'instance  
 Vous pouvez également manipuler des chaînes avec les méthodes de la classe `String`.  Les deux types de méthodes de `String` sont les suivantes : les méthodes *partagées* et les méthodes d'*instance*.  
  
#### Méthodes partagées  
 Une méthode partagée est issue de la classe `String` et ne nécessite pas une instance de cette classe.  Ces méthodes peuvent être désignées par le nom de la classe \(`String`\) plutôt que par une instance de la classe `String`.  Par exemple :  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 Dans l'exemple précédent, la méthode <xref:System.String.Copy%2A?displayProperty=fullName> est une méthode statique, qui agit sur une expression qui lui est attribuée et qui assigne le résultat à `bString`.  
  
#### Méthodes d'instance  
 En revanche, les méthodes d'instance proviennent d'une instance particulière de `String` et doivent être désignées par le nom de l'instance.  Par exemple :  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Dans cet exemple, la méthode <xref:System.String.Substring%2A?displayProperty=fullName> est une méthode de l'instance de `String` \(c'est\-à\-dire `aString`\).  Elle effectue une opération sur `aString` et assigne la valeur à `bString`.  
  
 Pour plus d'informations, consultez la documentation de la classe <xref:System.String>.  
  
## Voir aussi  
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)