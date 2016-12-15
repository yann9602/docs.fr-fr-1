---
title: "Long Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Long"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, &"
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "& identifier type character"
  - "integer numbers"
  - "literal type characters, L"
  - "numbers, integer"
  - "integers, data types"
  - "L literal type character"
  - "integers, types"
  - "Long keyword"
  - "data types [Visual Basic], integral"
  - "data types [Visual Basic], assigning"
  - "Long data type"
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Long Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 64 bits \(8 octets\) signés dont la valeur est comprise entre \-9 223 372 036 854 775 808 et 9 223 372 036 854 775 807 \(9 2...E\+18\).  
  
## Notes  
 Utilisez le type de données `Long` pour contenir des nombres entiers qui sont trop grands pour le type de données `Integer`.  
  
 La valeur par défaut de `Long` est 0.  
  
## Conseils de programmation  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que `Long` possède une largeur de données différente \(32 bits\) dans d'autres environnements.  Si vous passez un argument de 32 bits à un tel composant, déclarez\-le comme type de données `Integer` et non comme `Long` dans votre nouveau code Visual Basic.  
  
     En outre, l'Automatisation ne prend pas en charge les nombres entiers 64 bits sur Windows 95, Windows 98, Windows ME ou Windows 2000.  Vous ne pouvez pas passer d'argument `Long` Visual Basic à un composant Automation sur ces systèmes d'exploitation.  
  
-   **Extension.** Le type de données `Long` s'étend à `Decimal`, `Single` ou `Double`.  Ceci signifie que vous pouvez convertir `Long` en un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `L` à un littéral force ce dernier en un type de données `Long`.  L'ajout du caractère de type d'identificateur `&` à un identificateur force ce dernier en un type `Long`.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int64?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Int64>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)