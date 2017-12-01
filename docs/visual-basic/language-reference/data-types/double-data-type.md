---
title: "Double, type de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a>Double, type de données (Visual Basic)
Contient IEEE 64 bits (8 octets) double précision à virgule flottante des nombres signés dont la valeur de - 1, 79769313486231570E + 308 à - 4, 94065645841246544E-324 pour les valeurs négatives et entre 4, 94065645841246544E-324 à 1, 79769313486231570E + 308 pour valeurs positives. Nombres en double précision stockent une approximation d’un nombre réel.  
  
## <a name="remarks"></a>Remarques  
 Le `Double` type de données fournit les amplitudes les plus grandes et plus petit possibles pour un nombre.  
  
 La valeur par défaut de `Double` est 0.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Précision.** Lorsque vous travaillez avec des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours de représentation précise dans la mémoire. Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les `Mod` opérateur. Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
-   **Les zéros à droite.** Les types de données à virgule flottante n’ont pas une représentation interne de zéro caractère de fin. Par exemple, ils n’effectuent pas distinction entre 4,2000 et 4.2. Par conséquent, zéro caractères de fin n’apparaissent pas lorsque vous affichez ou des valeurs à virgule flottante d’impression.  
  
-   **Caractères de type.** L'ajout du caractère de type littéral `R` à un littéral force ce dernier en type de données `Double`. Par exemple, si une valeur entière est suivie `R`, la valeur est modifiée pour un `Double`.  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     L'ajout du caractère de type identificateur `#` à un identificateur force ce dernier en type `Double`. Dans l’exemple suivant, la variable `num` est typé comme un `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Double?displayProperty=nameWithType>  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [Single (type de données)](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
