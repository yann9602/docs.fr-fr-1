---
title: "Types de donn&#233;es en Visual Basic | Microsoft Docs"
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
  - "types de données [Visual Basic], déclarer"
  - "typage"
  - "types de données (Visual Basic)"
  - "code Visual Basic, types de données"
  - "types de données [Visual Basic], améliorer la vitesse avec"
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Types de donn&#233;es en Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Le *type de données* détermine la nature des données que peut contenir un élément de programmation et la manière dont il enregistre ces données.  Les types de données s'appliquent à toutes les valeurs susceptibles d'être enregistrées dans la mémoire d'un ordinateur ou d'intervenir dans l'évaluation d'une expression.  Chaque variable, littéral, constante, énumération, propriété, paramètre de procédure, argument de procédure et valeur de retour de procédure possède un type de données.  
  
## Types de données déclarés  
 Un élément de programmation est défini dans une instruction de déclaration et son type de données est spécifié à l'aide de la clause `As`.  Le tableau suivant présente les instructions que vous utilisez pour déclarer divers éléments.  
  
|Élément de programmation|Déclaration de type de données|  
|------------------------------|------------------------------------|  
|Variable|Dans une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|Avec un caractère de type de littéral ; consultez « Caractères de type de littéral » dans [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Constante|Dans [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Énumération|Dans [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Propriété|Dans une [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Paramètre de procédure|Dans [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md), [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md), ou [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument de procédure|Dans le code appelant ; chaque argument est un élément de programmation qui a déjà été déclaré, ou une expression qui contient des éléments déclarés<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Valeur de retour de procédure|Dans [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) ou [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Pour une liste des types de données Visual Basic, consultez [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Voir aussi  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Types génériques Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)