---
title: "Types de données en Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: c86e1bfacbe06d10915bd476a5c6f528fcebe70d
ms.openlocfilehash: 2642145e496469eb8bcb382408fda2147f48b0d5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/30/2017

---
# <a name="data-types-in-visual-basic"></a>Types de données en Visual Basic
Le *type de données* d’un élément de programmation fait référence au type de données qu’il peut contenir et à la façon dont il stocke ces données. Les types de données s’appliquent à toutes les valeurs qui peuvent être stockées dans la mémoire de l’ordinateur ou qui participent à l’évaluation d’une expression. Chaque variable, littéral, constante, énumération, propriété, paramètre de procédure, argument de procédure et valeur de retour de procédure possède un type de données.  
  
## <a name="declared-data-types"></a>Types de données déclarés  
 Vous définissez un élément de programmation avec une instruction de déclaration et spécifiez son type de données avec la clause `As`. Le tableau suivant présente les instructions que vous utilisez pour déclarer divers éléments.  
  
|Élément de programmation|Déclaration de type de données|  
|-------------------------|---------------------------|  
|Variable|Dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|Avec un caractère de type de littéral ; consultez « Caractères de type de littéral » dans [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Constante|Dans une [instruction Const](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Énumération|Dans une instruction [Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Propriété|Dans une [instruction Property](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Paramètre de procédure|Dans une [instruction Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), une [instruction Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou une [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument de procédure|Dans le code appelant ; chaque argument est un élément de programmation qui a déjà été déclaré, ou une expression qui contient des éléments déclarés<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Valeur de retour de procédure|Dans une [instruction Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou une [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Pour obtenir la liste des types de données Visual Basic, consultez [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversions de type en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tuples](tuples.md)     
 [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Utilisation efficace des types de données](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
