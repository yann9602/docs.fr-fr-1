---
title: "Numeric Data Types (Visual Basic) | Microsoft Docs"
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
  - "integral types, Visual Basic"
  - "Short data type, numeric data types"
  - "Double data type, numeric data types"
  - "Long data type, Visual Basic numeric data types"
  - "numbers, whole"
  - "fractions"
  - "numbers"
  - "whole numbers"
  - "integer numbers"
  - "numbers, integer"
  - "fractional data types"
  - "mantissas, of fractional numbers"
  - "mantissas"
  - "data types [Visual Basic], numeric"
  - "Integer data type, numeric data types"
  - "exponent, of fractional numbers"
  - "integers"
  - "numeric data types, Visual Basic"
  - "Single data type, numeric types"
  - "Decimal data type, numeric data types"
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Numeric Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] met à votre disposition plusieurs *types de données numériques* permettant de gérer les nombres dans diverses représentations.  Les types *intégraux* ne représentent que les nombres entiers \(positifs, négatifs et zéro\), tandis que les types *non intégraux* représentent les nombres composés d'une partie entière et d'une partie fractionnaire.  
  
 Pour consulter un tableau présentant une comparaison côte à côte des types de données de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], consultez [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Types numériques intégraux  
 Les *types de données intégraux* sont ceux qui ne représentent que des nombres sans partie fractionnaire.  
  
 Les types de données intégraux *signés* sont [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) \(8 bits\), [Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) \(16 bits\), [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) \(32 bits\) et [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) \(64 bits\).  Si une variable enregistre toujours des nombres entiers plutôt que des nombres fractionnaires, déclarez\-la avec l'un de ces types.  
  
 Les types intégraux *non signés* sont [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) \(8 bits\), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) \(16 bits\), [UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) \(32 bits\) et [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) \(64 bits\).  Si une variable contient des données binaires ou des données de nature inconnue, déclarez\-la avec l'un de ces types.  
  
### Performances  
 Les opérations arithmétiques sont plus rapides avec les types intégraux qu'avec les autres types de données.  Ils sont plus rapides avec les types `Integer` et `UInteger` dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
### Grands entiers  
 Si vous devez maintenir un entier plus grand que le type de données `Integer` peut contenir, vous pouvez utiliser à la place le type de données `Long`.  Les variables `Long` peuvent contenir des nombres de \-9,223,372,036,854,775,808 à 9,223,372,036,854,775,807.  Les opérations avec `Long` sont légèrement plus lentes qu'avec `Integer`.  
  
 Si vous avez besoin de valeurs encore plus grandes, vous pouvez utiliser le [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md).  Vous pouvez placer des nombres compris entre \-79 228 162 514 264 337 593 543 950 335 et 79 228 162 514 264 337 593 543 950 335 dans une variable `Decimal` si vous n'utilisez pas de décimales.  Toutefois, les opérations avec les nombres `Decimal` sont considérablement plus lentes qu'avec tout autre type de données numériques.  
  
### Petits entiers  
 Si vous n'avez pas besoin de la plage complète du type de données `Integer`, vous pouvez utiliser le type de données `Short` qui peut contenir des entiers de \-32,768 à 32,767.  Pour la plus petite plage d'entiers, le type de données `SByte` contient des entiers de \-128 à 127.  Si vous avez un même grand nombre des variables qui contiennent de petits entiers, le common language runtime peut quelquefois stocker plus efficacement vos variables `Short` et `SByte` et réduire la consommation de mémoire.  Toutefois, les opérations avec `Short` et `SByte` sont un peu plus lentes qu'avec `Integer`.  
  
### Entiers non signés  
 Si vous savez que votre variable ne contiendra jamais de nombre négatif, vous pouvez utiliser les *types non signés* `Byte`, `UShort`, `UInteger` et `ULong`.  Chacun de ces types de données peut contenir un entier positif deux fois plus grand que son type signé correspondant \(`SByte`, `Short`, `Integer` et `Long`\).  En termes de performances, chaque type non signé est exactement aussi efficace que son type signé correspondant.  En particulier, `UInteger` partage avec `Integer` la distinction d'être le plus efficace de tous les types de données numériques élémentaires.  
  
## Types numériques non intégraux  
 Les *types de données non intégraux* représentent des nombres composés d'une partie entière et d'une partie fractionnaire.  
  
 Les types de données numériques non intégraux sont `Decimal` \(128 bits virgule fixe\), [Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) \(32 bits virgule flottante\) et [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) \(64 bits virgule flottante\).  Tous ces types sont signés.  Si une variable peut contenir une fraction, déclarez\-la avec l'un de ces types.  
  
 `Decimal` n'est pas un type de données à virgule flottante.  Les numéros `Decimal` ont une valeur de nombre entier binaire et un facteur d'échelle entier qui spécifient quelle partie de la valeur est une fraction décimale.  
  
 Vous pouvez utiliser des variables d' `Decimal` pour les valeurs monétaires.  l'avantage est la précision des valeurs.  Le type de données `Double` est plus rapide et requiert moins de mémoire, mais il est soumis aux erreurs d'arrondi.  Le type de données d' `Decimal` conserve l'exactitude totale à 28 décimales.  
  
 Les nombres à virgule flottante \(`Single` et `Double`\) présentent des plages plus larges que les nombres de type `Decimal`, mais ils peuvent être sujets aux erreurs d'arrondi.  Les types à virgule flottante prennent en charge un nombre de chiffres significatifs inférieur à celui du type `Decimal`, mais ils peuvent représenter des valeurs d'amplitude supérieure.  
  
 Les valeurs de nombres non intégraux peuvent être exprimées comme mmmEeee, où mmm est la *mantisse* \(les bits significatifs\) et eee est l'*exposant* \(une puissance de 10\).  Les valeurs positives les plus élevées des types non intégraux sont 7,9228162514264337593543950335E\+28 pour `Decimal`, 3,4028235E\+38 pour `Single` et 1,79769313486231570E\+308 pour `Double`.  
  
### Performances  
 `Double` est le plus efficace des types de données fractionnaires, car les processeurs des plateformes actuelles exécutent les opérations en virgule flottante en double précision.  Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu'avec les types intégraux, tels que `Integer`.  
  
### Petites amplitudes  
 Pour les nombres avec la plus petite amplitude possible \(le plus proche de 0\), les variables `Double` peuvent contenir des nombres aussi petits que \-4,94065645841246544E\-324 pour les valeurs négatives et 4,94065645841246544E\-324 pour les valeurs positives.  
  
### Petits nombres fractionnaires  
 Si vous n'avez pas besoin de la plage complète du type de données `Double`, vous pouvez utiliser le type de données `Single` qui peut contenir des nombres à virgule flottante de \-3.4028235E\+38 à 3.4028235E\+38.  Les plus petites amplitudes pour les variables `Single` sont \-1.401298E\-45 pour les valeurs négatives et 1.401298E\-45 pour les valeurs positives.  Si vous avez un grand nombre de variables qui contiennent de petits nombres à virgule flottante, le Common Language Runtime peut quelquefois stocker plus efficacement vos variables `Single` et réduire la consommation de mémoire.  
  
## Voir aussi  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Miscellaneous Data Types](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)