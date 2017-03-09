---
title: "How to: Iterate Through An Enumeration in Visual Basic | Microsoft Docs"
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
  - "arrays [Visual Basic], iterating"
  - "enumerations [Visual Basic], iterating"
  - "ListBox control [Windows Forms], populating from an enumeration"
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Iterate Through An Enumeration in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les énumérations offrent un moyen pratique d'utiliser des ensembles de constantes connexes et d'associer des valeurs de constantes à des noms.  Pour itérer au sein d'une énumération, vous pouvez la déplacer dans un tableau à l'aide de la méthode <xref:System.Enum.GetValues%2A>.  Vous pourriez également itérer au sein d'une énumération à l'aide d'une instruction `For...Each`, en utilisant la méthode <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> pour extraire la chaîne ou valeur numérique.  
  
### Pour itérer au sein d'une énumération  
  
-   Déclarez un tableau et convertissez l'énumération en ce tableau avec la méthode <xref:System.Enum.GetValues%2A>, avant de passer le tableau comme vous le feriez avec toute autre variable.  L'exemple suivant affiche chaque membre de l'énumération <xref:Microsoft.VisualBasic.FirstDayOfWeek> qui itère au sein de l'énumération.  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#7)]  
  
## Voir aussi  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)