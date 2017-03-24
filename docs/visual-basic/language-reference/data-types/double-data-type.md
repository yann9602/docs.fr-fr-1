---
title: "Double Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Double"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, #"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "0 characters, trailing"
  - "literal type characters, R"
  - "data types [Visual Basic], assigning"
  - "Double data type [Visual Basic]"
  - "# identifier type character"
  - "double-precision numbers"
  - "floating-point numbers, Double data type"
  - "R literal type character"
  - "zeros, trailing"
  - "Double data type"
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Double Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Contient des nombres à virgule flottante en double précision IEEE 64 bits \(8 octets\) signés dont la valeur est comprise entre \-1,79769313486231570E\+308 et \-4,94065645841246544E\-324 pour les valeurs négatives et entre 4,94065645841246544E\-324 et 1,79769313486231570E\+308 pour les valeurs positives.  Les nombres en double précision stockent une approximation d'un nombre réel.  
  
## Notes  
 Le type de données `Double` fournit les amplitudes les plus grandes et les plus petites possibles pour un nombre.  
  
 La valeur par défaut de `Double` est 0.  
  
## Conseils de programmation  
  
-   **Précision.** Lorsque vous utilisez des nombres à virgule flottante, n'oubliez pas qu'ils n'ont pas toujours de représentation précise dans la mémoire.  Certaines opérations pourraient avoir des résultats inattendus, comme la comparaison de valeur et l'opérateur `Mod`.  Pour plus d'informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Zéros de fin.** Les types de données à virgule flottante n'ont aucune représentation interne du zéro \(0\) de fin.  Par exemple, ils ne font pas la différence entre 4,2000 et 4,2.  Par conséquent, le zéro \(0\) de fin n'apparaît pas lorsque vous affichez ou imprimez des valeurs à virgule flottante.  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `R` à un littéral force ce dernier en un type de données `Double`.  Par exemple, si une valeur entière est suivie de `R`, la valeur est remplacée par un `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     L'ajout du caractère de type d'identificateur `#` à un identificateur force ce dernier en un type `Double`.  Dans l'exemple suivant, la variable `num` est typée en tant que `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Double?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)