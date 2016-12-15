---
title: "Integer Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Integer"
  - "Integer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "enumerated values"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "literal type characters, I"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "% identifier type character"
  - "data types [Visual Basic], assigning"
  - "identifier type characters, %"
  - "I literal type character"
  - "Integer data type"
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Integer Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 32 bits \(4 octets\) signés dont la valeur est comprise entre \-2 147 483 648 et 2 147 483 647.  
  
## Notes  
 Le type de données `Integer` offre des performances optimales sur un processeur 32 bits.  Les autres types intégraux sont plus lents à charger et à stocker en provenance et à destination de la mémoire.  
  
 La valeur par défaut de `Integer` est 0.  
  
## Conseils de programmation  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que `Integer` possède une largeur de données différente \(16 bits\) dans les autres environnements.  Si vous passez un argument de 16 bits à un tel composant, déclarez\-le en tant que type de données `Short` et non `Integer` dans votre nouveau code Visual Basic.  
  
-   **Extension.** Le type de données `Integer` s'étend à `Long`, `Decimal`, `Single` ou `Double`.  Cela signifie que vous pouvez convertir `Integer` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout du caractère de type littéral `I` à un littéral force ce dernier en type de données `Integer`.  L'ajout du caractère de type identificateur `%` à un identificateur force ce dernier en type `Integer`.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int32?displayProperty=fullName>.  
  
## Plage  
 Si vous essayez d'assigner à une variable de type intégral un nombre situé hors de la plage de ce type, une erreur se produit.  Si vous essayez de lui assigner une fraction, le nombre est arrondi à la valeur entière supérieure ou inférieure la plus proche.  Si le nombre est proche à l'identique de deux valeurs entières, la valeur est arrondie à l'entier pair le plus proche.  Ce comportement réduit les erreurs d'arrondi qui résultent de l'arrondissement cohérent d'une valeur du milieu dans un seul sens.  Le code suivant présente des exemples d'arrondi.  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## Voir aussi  
 <xref:System.Int32?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)