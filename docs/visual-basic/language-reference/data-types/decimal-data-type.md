---
title: "Decimal Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Decimal"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, D"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "Decimal data type"
  - "D literal type character"
  - "decimals, Decimal data type"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "decimal keyword"
  - "numbers, real"
  - "variable-precision numbers"
  - "zeros, trailing"
  - "@ identifier type character"
  - "identifier type characters, @"
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Decimal Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Conserve les valeurs 128 bits \(16 octets\) qui représentent des entiers relatifs de 96 bits \(12 octets\) mis à l'échelle par une alimentation variable de 10.  Le facteur d'échelle spécifie le nombre de chiffres à droite de la virgule décimale ; il est compris entre 0 et 28.  La plus grande valeur possible avec une échelle 0 \(aucune décimale\) est \+\/\-79 228 162 514 264 337 593 543 950 335 \(\+\/\-7,9228162514264337593543950335E\+28\).  Avec 28 décimales, la plus grande valeur est \+\/\-7,9228162514264337593543950335, et la plus petite valeur différente de zéro est \+\/\-0,0000000000000000000000000001 \(\+\/\-1E\-28\).  
  
## Notes  
 Le type de données `Decimal` fournit le plus grand nombre de chiffres significatifs pour un nombre.  Il prend en charge jusqu'à 29 chiffres significatifs et peut représenter des valeurs supérieures à 7.9228 x 10^28.  Ce type de données est particulièrement adapté aux calculs \(par exemple, financiers\) qui exigent un grand nombre de chiffres, mais qui ne peuvent pas tolérer les erreurs d'arrondi.  
  
 La valeur par défaut de `Decimal` est 0.  
  
## Conseils de programmation  
  
-   **Précision.** `Decimal` n'est pas un type de données à virgule flottante.  La structure `Decimal` contient une valeur entière binaire, avec un bit de signe et un facteur d'échelle d'entier qui spécifie quelle partie de la valeur est une fraction décimale.  C'est pourquoi les nombres `Decimal` ont une représentation plus précise dans la mémoire que les types à virgule flottante \(`Single` et `Double`\).  
  
-   **Performances.** Le type de données `Decimal` est le plus lent de tous les types numériques.  Vous devez peser l'importance de la précision par rapport aux performances avant de choisir un type de données.  
  
-   **Extension.** Le type de données `Decimal` s'étend à `Single` ou `Double`.  Cela signifie que vous pouvez convertir des données de type `Decimal` en données de l'un ou l'autre de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Zéros de fin.** Visual Basic ne stocke pas de zéros de fin dans un littéral `Decimal`.  Toutefois, une variable `Decimal` conserve tous les zéros de fin obtenus par le calcul.  L'exemple suivant illustre ce comportement.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     La sortie de `MsgBox` dans l'exemple précédent est la suivante :  
  
     d1 \= 2.375, d2 \= 1.625, d3 \= 4.000, d4 \= 4  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `D` à un littéral force ce dernier en un type de données `Decimal`.  L'ajout du caractère de type d'identificateur `@` à un identificateur force ce dernier en un type `Decimal`.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Decimal?displayProperty=fullName>.  
  
## Plage  
 Il est parfois nécessaire d'utiliser le caractère de type `D` pour assigner une grande valeur à une variable ou à une constante `Decimal`.  Cette spécification est que le compilateur interprète comme un littéral `Long` à moins qu'un caractère de type de littéral suive le littéral, comme le montre l'exemple suivant.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 La déclaration de `bigDec1` ne produit pas un dépassement car la valeur qui lui est assignée fait partie de la marge pour `Long`.  La valeur d' `Long` peut être assignée à la variable d' `Decimal` .  
  
 La déclaration de `bigDec2` génère une erreur de dépassement de capacité car la valeur qui lui est assignée est trop grande pour `Long`.  Étant donné que le littéral numérique ne peut pas d'abord être interprète comme `Long`, il ne peut pas être assigné à la variable d' `Decimal` .  
  
 Pour `bigDec3`, le caractère de type de littéral `D` résout le problème en forçant le compilateur pour interpréter le littéral comme `Decimal` et non comme `Long`.  
  
## Voir aussi  
 <xref:System.Decimal?displayProperty=fullName>   
 <xref:System.Decimal.%23ctor%2A?displayProperty=fullName>   
 <xref:System.Math.Round%2A?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)