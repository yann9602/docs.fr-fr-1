---
title: "Types de données des résultats d’opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types
- operator result data types
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 577be6330cb76da436470c383841a717dd6e3200
ms.lasthandoff: 03/13/2017

---
# <a name="data-types-of-operator-results-visual-basic"></a>Types de données des résultats d'opérateur (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Détermine le type de données de résultat d’une opération basée sur les types de données des opérandes. Dans certains cas, cela peut être un type de données avec une plage supérieure à celle de des opérandes.  
  
## <a name="data-type-ranges"></a>Plages de types de données  
 Les plages des types de données pertinents, dans l’ordre du plus petit au plus grand, sont les suivantes :  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — deux valeurs possibles  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [octets](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 valeurs intégrales possibles  
  
-   [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) : 65 536 (6.5... E + 4) valeurs intégrales possibles  
  
-   [Entier](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) : 4 294 967 296 (4.2... E + 9) valeurs intégrales possibles  
  
-   [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) valeurs intégrales possibles  
  
-   [Décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) : 1,5... E + 29 valeurs intégrales possibles, nombre maximales de plage 7.9... E + 28 (valeur absolue)  
  
-   [Seul](../../../visual-basic/language-reference/data-types/single-data-type.md) : plage maximale est 3,4... E + 38 (valeur absolue)  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) : plage maximale est 1,7... E + 308 (valeur absolue)  
  
 Pour plus d’informations sur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] des types de données, consultez [des Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Si un opérande a la valeur [rien](../../../visual-basic/language-reference/nothing.md), le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] opérateurs arithmétiques considèrent comme égales à zéro.  
  
## <a name="decimal-arithmetic"></a>Arithmétique décimale  
 Notez que la [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) type de données n’est ni à virgule flottante, ni entier.  
  
 Si des opérandes d’une `+`, `–`, `*`, `/`, ou `Mod` opération `Decimal` et l’autre n’est pas `Single` ou `Double`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] étend l’autre opérande à `Decimal`. Il effectue l’opération dans `Decimal`, et le type de données de résultat est `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Arithmétique à virgule flottante  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]effectue la plupart des arithmétique à virgule flottante dans [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), qui est les plus efficace des données de type pour ces opérations. Toutefois, si un opérande est [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) et l’autre n’est pas `Double`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] effectue l’opération dans `Single`. Il élargit chaque opérande si nécessaire, pour le type de données approprié avant l’opération, et le résultat est du même type de données.  
  
### <a name="-and--operators"></a>/ et ^ opérateurs  
 Le `/` opérateur est défini uniquement pour le [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [unique](../../../visual-basic/language-reference/data-types/single-data-type.md), et [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) des types de données. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]élargit chaque opérande si nécessaire, pour le type de données approprié avant l’opération et le résultat est du même type de données.  
  
 Le tableau suivant montre le résultat de types de données pour le `/` opérateur. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérande, le type de données de résultat est le même quel que soit l’ordre des opérandes.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Un type d’entier|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Un type d’entier|Decimal|Single|Double|Double|  
  
 Le `^` opérateur est défini uniquement pour la `Double` type de données. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]élargit chaque opérande correctement à `Double` avant l’opération et le résultat de type de données est toujours `Double`.  
  
## <a name="integer-arithmetic"></a>Arithmétique sur les entiers  
 Le type de données de résultat d’une opération entier varie selon les types de données des opérandes. En règle générale, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilise les stratégies suivantes pour déterminer le type de données de résultat :  
  
-   Si les deux opérandes d’un opérateur binaire ont le même type de données, le résultat est du même type de données. Une exception est `Boolean`, qui est forcé à `Short`.  
  
-   Si un opérande non signé est inclus avec un opérande signé, le résultat est un type signé au moins aussi grande une plage en tant que des opérandes.  
  
-   Sinon, le résultat est généralement le plus grand des deux types de données d’opérande.  
  
 Notez que le type de données de résultat ne peut pas être identique à un type de données d’opérande.  
  
> [!NOTE]
>  Le type de données de résultat n’est pas toujours suffisamment grand pour contenir toutes les valeurs possibles résultant de l’opération. Un <xref:System.OverflowException>exception peut se produire si la valeur est trop grande pour le type de données de résultat.</xref:System.OverflowException>  
  
### <a name="unary--and--operators"></a>Unaire + et -les opérateurs  
 Le tableau suivant présente les types de données du résultat pour les opérateurs unaires, `+` et `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unaire`+`|Short|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|Unaire`–`|Short|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\<et >> opérateurs  
 Le tableau suivant présente les types de données du résultat pour les deux opérateurs de décalage de bits, `<<` et `>>`. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]traite chaque opérateur de décalage de bits comme un opérateur unaire sur son opérande gauche (modèle binaire à décaler).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
  
 Si l’opérande de gauche est `Decimal`, `Single`, `Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente du convertir en `Long` avant l’opération et le résultat est de type de données `Long`. L’opérande droit (le nombre de positions de bits à décaler) doit être `Integer` ou un type qui s’étend à `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binaire +, -, * et les opérateurs Mod  
 Le tableau suivant montre le résultat de types de données pour le fichier binaire `+` et `–` opérateurs et `*` et `Mod` opérateurs. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérande, le type de données de résultat est le même quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`Byte`|Courte|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Courte|Short|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Decimal|  
|`UInteger`|Longue|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Longue|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\, opérateur  
 Le tableau suivant montre le résultat de types de données pour le `\` opérateur. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérande, le type de données de résultat est le même quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Short|Short|Entier|Entier|Long|Long|Longue|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Longue|  
|`Byte`|Courte|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Courte|Short|Short|Short|Entier|Entier|Long|Long|Longue|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Longue|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si des opérandes de le `\` opérateur est [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [unique](../../../visual-basic/language-reference/data-types/single-data-type.md), ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente du convertir en [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) avant l’opération et le résultat est de type de données `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparaisons relationnelles et au niveau du bit  
 Le type de données de résultat d’une opération relationnelle (`=`, `<>`, `<`, `>`, `<=`, `>=`) est toujours `Boolean` [Type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Cela vaut pour les opérations logiques (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) sur `Boolean` opérandes.  
  
 Le type de données de résultat d’une opération logique au niveau du bit varie selon les types de données des opérandes. Notez que `AndAlso` et `OrElse` sont définis uniquement pour `Boolean`, et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit chaque opérande si nécessaire en `Boolean` avant d’effectuer l’opération.  
  
### <a name="-----and--operators"></a>=, <>, \<, >, \<=, and >= Operators  
 Si les deux opérandes sont `Boolean`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considère `True` être inférieur à `False`. Si un type numérique est comparé à un `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de convertir la `String` à `Double` avant l’opération. A `Char` ou `Date` opérande peut être comparé qu’avec un autre opérande du même type de données. Le type de données de résultat est toujours `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Opérateur de bits Not (opérateur)  
 Le tableau suivant montre le résultat de l’opérateur de bits des types de données `Not` opérateur.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Booléen|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
  
 Si l’opérande est `Decimal`, `Single`, `Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente du convertir en `Long` avant l’opération et le résultat est de type de données `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Au niveau du bit et, ou et les opérateurs Xor  
 Le tableau suivant montre le résultat de l’opérateur de bits des types de données `And`, `Or`, et `Xor` opérateurs. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérande, le type de données de résultat est le même quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Booléen|SByte|Short|Short|Entier|Entier|Long|Long|Longue|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Longue|  
|`Byte`|Courte|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Courte|Short|Short|Short|Entier|Entier|Long|Long|Longue|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Longue|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si un opérande est `Decimal`, `Single`, `Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tente du convertir en `Long` avant l’opération et les données de résultat type est le même que si cet opérande était déjà `Long`.  
  
## <a name="miscellaneous-operators"></a>Opérateurs divers  
 Le `&` opérateur est défini uniquement pour la concaténation de `String` opérandes. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Convertit chaque opérande si nécessaire en `String` avant l’opération et le résultat de type de données est toujours `String`. Dans le cadre de la `&` opérateur, toutes les conversions en `String` sont considérées comme des étendues, même si `Option Strict` est `On`.  
  
 Le `Is` et `IsNot` opérateurs requièrent les deux opérandes soient d’un type référence. The `TypeOf`... `Is` expression requiert que le premier opérande soit d’un type référence et le deuxième opérande par le nom d’un type de données. Dans tous les cas les données de résultat est type `Boolean`.  
  
 Le `Like` opérateur est défini uniquement pour les critères spéciaux de `String` opérandes. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]essaie de convertir chaque opérande si nécessaire en `String` avant l’opération. Le type de données de résultat est toujours `Boolean`.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Opérateurs et Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Opérateurs](../../../visual-basic/language-reference/operators/index.md)   
 [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
