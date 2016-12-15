---
title: "Data Types of Operator Results (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "data types [Visual Basic], operator result data types"
  - "result data types"
  - "operator result data types"
  - "operators [Visual Basic], data types"
  - "data types [Visual Basic], ranges"
  - "operators [Visual Basic], result data types"
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Data Types of Operator Results (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] détermine le type de données de résultat d'une opération à partir des types de données des opérandes.  Dans certains cas, il peut s'agir d'un type de données disposant d'une plage plus grande que celle d'un opérande.  
  
## Plages des types de données  
 Les plages des types de données pertinents, dans l'ordre croissant de taille, sont les suivantes :  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — deux valeurs possibles  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 valeurs intégrales possibles  
  
-   [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65 536 \(6,5... E\+4\) valeurs intégrales possibles  
  
-   [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 \(4,2... E\+9\) valeurs intégrales possibles  
  
-   [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18 446 744 073 709 551 615 \(1,8... E\+9\) valeurs intégrales possibles  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1,5... E\+29 valeurs intégrales possibles, la plage maximale est 7,9... E\+28 \(valeur absolue\)  
  
-   [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) — la plage maximale est 3,4 ... E\+38 \(valeur absolue\)  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — la plage maximale est 1,7 ... E\+308 \(valeur absolue\)  
  
 Pour plus d'informations sur les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consultez [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Si un opérande prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), les opérateurs arithmétiques [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] la considèrent comme étant égale à zéro.  
  
## Arithmétique décimale  
 Notez que le type de données [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) n'est ni à virgule flottante, ni entier.  
  
 Si un opérande d'une opération `+`, `–,` `*,` `/, ou` `Mod est de type` `Decimal et que l'autre n'est pas` `Single ou` `Double,` [!INCLUDE[vbprvb étend l'autre opérande à]()]`Decimal`.  Il effectue l'opération en `Decimal` et le type de données de résultat est `Decimal`.  
  
## Arithmétique à virgule flottante  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] exécute la plupart des opérations arithmétiques à virgule flottante en [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), qui est le type de données le plus efficace pour ce genre d'opérations.  Toutefois, si un opérande est [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) et que l'autre n'est pas `Double`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] effectue l'opération en `Single`.  Il étend si nécessaire chaque opérande au type de données approprié avant l'opération, et le résultat est du même type de données.  
  
### Opérateurs \/ et ^  
 L'opérateur `/` est défini uniquement pour les types de données [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) et [Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] étend si nécessaire chaque opérande au type de données approprié avant l'opération, et le résultat est du même type de données.  
  
 Le tableau suivant présente les types de données de résultat pour l'opérateur `/`.  Notez que ce tableau est symétrique ; pour une combinaison de types de données d'opérande spécifiée, le type de données de résultat est le même, quel que soit l'ordre des opérandes.  
  
||||||  
|-|-|-|-|-|  
||`Decimal`|`Single`|`Double`|Tout type d'entier|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Tout type d'entier|Decimal|Single|Double|Double|  
  
 L'opérateur `^` est défini uniquement pour le type de données `Double`.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] élargit chaque opérande correctement à `Double` avant l'opération, et le type de données de résultat est toujours `Double`.  
  
## Arithmétique sur les entiers  
 Le type de données de résultat d'une opération sur des entiers dépend des types de données des opérandes.  En général, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilise les stratégies suivantes pour déterminer le type de données de résultat :  
  
-   Si les deux opérandes d'un opérateur binaire ont le même type de données, le résultat sera également de ce type de données.  `Boolean` fait exception ; il est forcé en `Short`.  
  
-   Si un opérande non signé est associé à un opérande signé, le résultat est d'un type signé assorti d'une plage au moins aussi grande que l'un des opérandes.  
  
-   Sinon, le résultat prend généralement le plus grand des deux types de données d'opérande.  
  
 Notez que le type de données de résultat peut ne pas être le même que celui des opérandes.  
  
> [!NOTE]
>  En effet, le type de données de résultat n'est pas toujours assez grand pour contenir toutes les valeurs possibles résultant de l'opération.  Une exception <xref:System.OverflowException> peut se produire si la valeur est trop grande pour le type de données de résultat.  
  
### Opérateurs unaires \+ et \-  
 Le tableau suivant présente les types de données de résultat pour les deux opérateurs unaires, `+` et `–`.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`+` unaire|Short|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`–` unaire|Short|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
  
### Opérateurs \<\< et \>\>  
 Le tableau suivant présente les types de données de résultat pour les opérateurs binaires, `<<` et `>>`.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] traite chaque opérateur de décalage de bits comme un opérateur unaire sur son opérande gauche \(modèle binaire à déplacer\).  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
  
 Si l'opérande gauche est de type `Decimal`, `Single`, `Double` ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de le convertir en `Long` avant l'opération, et le type de données de résultat est `Long`.  L'opérande droit \(le nombre de positions binaires à décaler\) doit être `Integer` ou d'un type qui s'étend à `Integer`.  
  
### Opérateurs binaires \+ et –, et opérateurs \* et Mod  
 Le tableau suivant présente les types de données de résultat pour les opérateurs binaires `+` et `– et les opérateurs` `*` et `Mod`.  Notez que ce tableau est symétrique ; pour une combinaison de types de données d'opérande spécifiée, le type de données de résultat est le même, quel que soit l'ordre des opérandes.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`Byte`|Short|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Entier|Entier|Long|Long|Decimal|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### \\, opérateur  
 Le tableau suivant présente les types de données de résultat pour l'opérateur `\`.  Notez que ce tableau est symétrique ; pour une combinaison de types de données d'opérande spécifiée, le type de données de résultat est le même, quel que soit l'ordre des opérandes.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Entier|Entier|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Entier|Entier|Long|Long|Long|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si l'un des opérandes de l'opérateur `\ est` Decimal[,](../../../visual-basic/language-reference/data-types/decimal-data-type.md)Single[ou](../../../visual-basic/language-reference/data-types/single-data-type.md)Double[,](../../../visual-basic/language-reference/data-types/double-data-type.md)[!INCLUDE[vbprvb essaie de le convertir en]()]Long[avant l'opération, et le type de données de résultat est](../../../visual-basic/language-reference/data-types/long-data-type.md)`Long`.  
  
## Comparaison de bits et comparaison relationnelle  
 Le type de données de résultat d'une opération relationnelle \(`=`, `<>`, `<`, `>`, `<=`, `>=`\) est toujours `Boolean`[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  Il en va de même pour les opérations logiques \(`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`\) sur les opérandes `Boolean`.  
  
 Le type de données de résultat d'une opération logique de bits dépend des types de données des opérandes.  Notez que `AndAlso` et `OrElse` sont définis uniquement pour `Boolean` et que [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit si nécessaire chaque opérande en `Boolean` avant d'effectuer l'opération.  
  
### Opérateurs \=, \<\>, \<, \>, \<\= et \>\=  
 Si les deux opérandes sont `Boolean`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considère que la valeur `True` est inférieure à `False`.  Si un type numérique est comparé à un `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de convertir le `String` en `Double` avant l'opération.  Une comparaison avec un opérande de type `Char` ou `Date` ne peut être établie qu'avec un autre opérande du même type de données.  Le type de données de résultat est toujours `Boolean`.  
  
### Opérateur de bits NOT  
 Le tableau suivant présente les types de données de résultat pour l'opérateur de bits `Not`.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
  
 Si l'opérande est de type `Decimal`, `Single`, `Double` ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de le convertir en `Long` avant l'opération, et le type de données de résultat est `Long`.  
  
### Opérateurs de bits AND, OR et XOR  
 Le tableau suivant présente les types de données de résultat pour les opérateurs de bits `And`, `Or` et `Xor`.  Notez que ce tableau est symétrique ; pour une combinaison de types de données d'opérande spécifiée, le type de données de résultat est le même, quel que soit l'ordre des opérandes.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Short|Short|Entier|Entier|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Entier|Entier|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Entier|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Entier|Entier|Long|Long|Long|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Long|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si un opérande est `Decimal`, `Single`, `Double` ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de le convertir en `Long` avant l'opération, et le type de données de résultat est le même que si cet opérande était déjà de type `Long`.  
  
## Opérateurs divers  
 L'opérateur `&` est défini uniquement pour la concaténation d'opérandes `String`.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit chaque opérande correctement en `String` avant l'opération, et le type de données de résultat correspond toujours à `String`.  Pour les besoins de l'opérateur `&`, toutes les conversions en `String` sont considérées comme étant étendues, même si `Option Strict` est `On`.  
  
 Les opérateurs `Is` et `IsNot` exigent que les deux opérandes soient d'un type référence.  L'expression `TypeOf`...`Is` exige que le premier opérande soit d'un type référence et que le second opérande représente le nom d'un type de données.  Dans tous ces cas, le type de données de résultat est `Boolean`.  
  
 L'opérateur `Like` est défini uniquement pour les critères spéciaux d'opérandes `String`.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] essaie de convertir correctement chaque opérande en `String` avant l'opération.  Le type de données de résultat est toujours `Boolean`.  
  
## Voir aussi  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operators](../../../visual-basic/language-reference/operators/index.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)