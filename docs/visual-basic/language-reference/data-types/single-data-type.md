---
title: "Single Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Single"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Single data type"
  - "F literal type character"
  - "trailing zeros"
  - "real numbers"
  - "literal type characters, F"
  - "trailing 0 characters"
  - "identifier type characters, !"
  - "single-precision numbers"
  - "! identifier type character"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "floating-point numbers, Single data type"
  - "numbers, real"
  - "zeros, trailing"
  - "numbers, floating point"
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Single Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des nombres à virgule flottante en simple précision IEEE 32 bits \(4 octets\) signés dont la valeur est comprise entre \-3,4028235E\+38 et \-1,401298E\-45 pour les valeurs négatives et entre 1,401298E\-45 et 3,4028235E\+38 pour les valeurs positives.  Les nombres en simple précision stockent une approximation d'un nombre réel.  
  
## Notes  
 Utilisez le type de données `Single` pour contenir des valeurs à virgule flottante qui ne nécessitent pas la largeur complète des données de type `Double`.  Dans certains cas, le Common Language Runtime peut être capable de comprimer les variables `Single` ensemble et d'enregistrer la consommation de mémoire.  
  
 La valeur par défaut de `Single` est 0.  
  
## Conseils de programmation  
  
-   **Précision.** Lorsque vous utilisez des nombres à virgule flottante, pensez qu'ils n'ont pas toujours de représentation précise dans la mémoire.  Certaines opérations pourraient avoir des résultats inattendus, comme la comparaison de valeur et l'opérateur `Mod`.  Pour plus d'informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Extension.** Le type de données `Single` s'étend à `Double`.  Cela signifie que vous pouvez convertir `Single` en `Double` sans produire d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Zéros de fin.** Les types de données à virgule flottante n'ont aucune représentation interne du 0 de fin.  Par exemple, ils ne font pas la différence entre 4,2000 et 4,2.  Par conséquent, le 0 de fin n'apparaît pas lorsque vous affichez ou imprimez des valeurs à virgule flottante.  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `F` à un littéral force ce dernier en un type de données `Single`.  L'ajout du caractère de type d'identificateur `!` à un identificateur force ce dernier en un type `Single`.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Single?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)