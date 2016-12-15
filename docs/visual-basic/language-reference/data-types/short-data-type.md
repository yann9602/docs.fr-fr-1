---
title: "Short Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Short"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "S literal type character"
  - "Short data type"
  - "literal type characters, S"
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Short Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 16 bits \(2 octets\) signés dont la valeur est comprise entre \-32,768 et 32,767.  
  
## Notes  
 Utilisez le type de données `Short` pour contenir des valeurs entières qui ne nécessitent pas la largeur complète des données de type `Integer`.  Dans certains cas, le Common Language Runtime peut comprimer les variables `Short` ensemble et d'enregistrer la consommation de mémoire.  
  
 La valeur par défaut de `Short` est 0.  
  
## Conseils de programmation  
  
-   **Extension.** Le type de données `Short` s'étend à `Integer`, `Long`, `Decimal`, `Single`, ou `Double`.  Ceci signifie que vous pouvez convertir `Short` en un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `S` à un littéral force ce dernier en un type de données `Short`.  `Short` n'a aucun caractère de type identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int16?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Int16?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)