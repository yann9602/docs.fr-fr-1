---
title: "Types de données numériques (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c185b7c04d589bfe74d1cca0c60df3e81ab80d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-data-types-visual-basic"></a>Types de données numériques (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]fournit plusieurs *types de données numériques* pour gérer les nombres dans diverses représentations. *Intégraux* représentent des types que des nombres entiers (positifs, négatifs et zéro), et *intégraux* types représentent les nombres entiers et des parties fractionnaires.  
  
 Pour un tableau montrant une comparaison côte-à-côte de la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] des types de données, consultez [des Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="integral-numeric-types"></a>Types numériques intégraux  
 *Types de données intégraux* sont ceux qui ne représentent que des nombres sans partie fractionnaire.  
  
 Le *signé* sont des types de données intégraux [Type de données SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bits), [Type de données Short](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bits), [Type de données Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32 bits) et [ Type de données long](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bits). Si une variable stocke toujours des nombres entiers plutôt que des nombres fractionnaires, déclarez-le en tant qu’un de ces types.  
  
 Le *non signé* sont des types intégraux [Type de données Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bits), [Type de données UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16 bits), [Type de données UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32 bits) et [ Type de données de ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bits). Si une variable contient des données binaires ou des données de nature inconnue, déclarez-le en tant qu’un de ces types.  
  
### <a name="performance"></a>Performances  
 Opérations arithmétiques sont plus rapides avec les types intégraux qu’avec d’autres types de données. Ils sont plus rapides avec les `Integer` et `UInteger` types dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="large-integers"></a>Entiers longs  
 Si vous avez besoin contenir un nombre entier supérieur à la `Integer` type de données peut contenir, vous pouvez utiliser la `Long` à la place du type de données. `Long`les variables peuvent contenir des nombres de -9,223,372,036,854,775,808 à 9,223,372,036,854,775,807. Les opérations avec `Long` sont légèrement plus lentes qu’avec `Integer`.  
  
 Si vous avez besoin de valeurs encore plus grandes, vous pouvez utiliser la [Type de données Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Vous pouvez stocker des nombres de-79,228,162,514,264,337,593,543,950,335 via 79,228,162,514,264,337,593,543,950,335 dans un `Decimal` variable si vous n’utilisez pas de n’importe quel nombre de décimales. Toutefois, les opérations avec `Decimal` numéros sont beaucoup plus lentes qu’avec tout autre type de données numériques.  
  
### <a name="small-integers"></a>Petits entiers  
 Si vous n’avez pas besoin de la plage complète de la `Integer` type de données, vous pouvez utiliser la `Short` type de données, qui peut contenir des nombres entiers compris entre-32 768 à 32 767. Pour la plus petite plage d’entiers, le `SByte` type de données conserve des entiers de -128 à 127. Si vous avez un très grand nombre de variables qui contiennent de petits entiers, le common language runtime peut quelquefois stocker votre `Short` et `SByte` variables plus efficacement et de réduire la consommation de mémoire. Toutefois, les opérations avec `Short` et `SByte` sont un peu plus lentes qu’avec `Integer`.  
  
### <a name="unsigned-integers"></a>Entiers non signés  
 Si vous savez que votre variable ne doit jamais contenir un nombre négatif, vous pouvez utiliser la *types non signés*`Byte`, `UShort`, `UInteger`, et `ULong`. Chacun de ces types de données peut contenir un entier positif deux fois plus grand que son type signé correspondant (`SByte`, `Short`, `Integer`, et `Long`). En termes de performances, chaque type non signé est exactement aussi efficace que son type signé correspondant. En particulier, `UInteger` partage avec `Integer` la distinction d’être le plus efficace de tous les types de données numériques élémentaires.  
  
## <a name="nonintegral-numeric-types"></a>Types numériques intégraux  
 *Types de données non intégraux* sont ceux qui représentent des nombres entière et fractionnaire.  
  
 Les types de données numériques non intégraux sont `Decimal` (128 bits virgule fixe) [unique Type de données](../../../../visual-basic/language-reference/data-types/single-data-type.md) (virgule flottante 32 bits), et [Type de données Double](../../../../visual-basic/language-reference/data-types/double-data-type.md) (virgule flottante de 64 bits). Elles sont toutes signées types. Si une variable peut contenir une fraction, déclarez-le en tant qu’un de ces types.  
  
 `Decimal`n’est pas un type de données à virgule flottante. `Decimal`nombres ont une valeur d’entier binaire et un facteur d’échelle entier qui spécifie quelle partie de la valeur est une fraction décimale.  
  
 Vous pouvez utiliser `Decimal` variables pour les valeurs monétaires. L’avantage est la précision des valeurs. Le `Double` type de données est plus rapide et nécessite moins de mémoire, mais il est soumis aux erreurs d’arrondi. Le `Decimal` type de données conserve l’exactitude totale à 28 décimales.  
  
 À virgule flottante (`Single` et `Double`) nombres ont des plages plus larges que `Decimal` des chiffres, mais peut être sujette à erreurs d’arrondi. Prend en charge les types à virgule flottante moins de chiffres significatifs que `Decimal` mais ils peuvent représenter des valeurs d’amplitude supérieure.  
  
 Les valeurs numériques non intégraux peuvent être exprimées comme mmmEeee, dans laquelle mmm est la *mantisse* (chiffres significatifs) et eee le *exposant* (il s’agit d’une puissance de 10). Les valeurs positives la plus élevées des types intégraux sont 7, 9228162514264337593543950335E + 28 pour `Decimal`, 3,4028235E + 38 pour `Single`et 1, 79769313486231570E + 308 pour `Double`.  
  
### <a name="performance"></a>Performances  
 `Double`est la plus efficace des types de données fractionnaires, car les processeurs sur les plateformes actuelles exécutent des opérations à virgule flottante à double précision. Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu’avec les types intégraux, tels que `Integer`.  
  
### <a name="small-magnitudes"></a>Petites amplitudes  
 Pour les nombres avec la plus petite amplitude possible (le plus proche de 0), `Double` variables peuvent contenir des nombres aussi petits que - 4, 94065645841246544E-324 pour les valeurs négatives et 4, 94065645841246544E-324 pour les valeurs positives.  
  
### <a name="small-fractional-numbers"></a>Petits nombres fractionnaires  
 Si vous n’avez pas besoin de la plage complète de la `Double` type de données, vous pouvez utiliser la `Single` type de données, qui peut contenir des nombres à virgule flottante compris entre - 3,4028235E + 38 et 3,4028235E + 38. Les plus petites amplitudes pour `Single` variables sont - 1.401298E-45 pour les valeurs négatives et 1.401298E-45 pour les valeurs positives. Si vous avez un grand nombre de variables qui contiennent de petits nombres à virgule flottante, le common language runtime peut quelquefois stocker votre `Single` variables plus efficacement et de réduire la consommation de mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Types de données caractère](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Types de données divers](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
