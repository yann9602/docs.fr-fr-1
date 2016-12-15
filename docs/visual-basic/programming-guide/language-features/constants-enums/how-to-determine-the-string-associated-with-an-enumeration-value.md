---
title: "How to: Determine the String Associated with an Enumeration Value (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic]"
  - "strings [Visual Basic], enumeration values"
  - "values, enumeration members"
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Determine the String Associated with an Enumeration Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les méthodes <xref:System.Enum.GetValues%2A> et <xref:System.Enum.GetNames%2A> vous permettent de déterminer les chaînes et valeurs associées à des membres d'énumération.  
  
### Pour déterminer la chaîne associée à une énumération  
  
-   Utilisez la méthode <xref:System.Enum.GetNames%2A> pour récupérer les chaînes associées aux membres d'énumération.  Cet exemple déclare une énumération, `flavorEnum`, puis utilise la méthode <xref:System.Enum.GetNames%2A> pour afficher les chaînes associées à chaque membre.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## Voir aussi  
 <xref:System.Enum.GetValues%2A>   
 <xref:System.Enum.GetNames%2A>   
 <xref:System.Enum>   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)