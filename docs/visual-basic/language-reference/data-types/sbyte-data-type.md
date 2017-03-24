---
title: "SByte Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.sbyte"
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
  - "SByte data type"
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# SByte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Contient des entiers 8 bits \(1 octet\) signés dont la valeur est comprise entre \-128 et 127.  
  
## Notes  
 Utilisez le type de données `SByte` pour contenir des valeurs entières qui ne requièrent pas la largeur totale des données de `Integer` ou même la moitié de la largeur des données de `Short`.  Dans certains cas, le Common Language Runtime peut être capable de comprimer les variables `SByte` ensemble et d'enregistrer la consommation de mémoire.  
  
 La valeur par défaut de `SByte` est 0.  
  
## Conseils de programmation  
  
-   **Conforme CLS.** Le type de données `SByte` ne faisant pas partie de [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md), le code conforme CLS ne peut pas consommer un composant qui l'utilise.  
  
-   **Extension.** Le type de données `SByte` s'étend à `Short`, `Integer`, `Long`, `Decimal`, `Single` et `Double`.  Ceci signifie que vous pouvez convertir `SByte` en ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.**  `SByte` n'a aucun caractère de type de littéral ou caractère de type d'identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.SByte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)