---
title: "Arithmetic Operators in Visual Basic | Microsoft Docs"
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
  - "type safety"
  - "operators [Visual Basic], bitwise"
  - "operators [Visual Basic], bit-shift"
  - "bitwise operators"
  - "bit-shift operators"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "division, by zero"
  - "Visual Basic code, operators"
  - "arithmetic operators, about arithmetic operators"
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Arithmetic Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les opérateurs arithmétiques permettent d'effectuer de nombreuses opérations arithmétiques familières qui impliquent le calcul de valeurs numériques représentées par des littéraux, des variables, d'autres expressions, des appels de fonction et de propriété et des constantes.  Également classés avec les opérateurs arithmétiques figurent les opérateurs de décalage de bits, qui agissent au niveau des bits des opérandes et décalent leurs modèles binaires vers la gauche ou vers la droite.  
  
## Opérations arithmétiques  
 Vous pouvez ajouter deux valeurs dans une expression à l'aide de l'[\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), ou soustraire une valeur d'une autre à l'aide de l'[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md), comme le montre l'exemple ci\-dessous.  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 La négation utilise également l'[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mais avec un seul opérande, comme le montre l'exemple ci\-dessous.  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 La multiplication et la division utilisent l'[\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) et l'[\/ Operator](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivement, comme le montre l'exemple ci\-dessous.  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 L'élévation à la puissance utilise l'[^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), comme le montre l'exemple ci\-dessous.  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 La division par un entier s'effectue à l'aide de l'[\\ Operator](../../../../visual-basic/language-reference/operators/integer-division-operator.md).  Elle retourne le quotient, c'est\-à\-dire l'entier qui représente le nombre de fois que le diviseur peut être divisé par le dividende sans tenir compte du reste.  Le diviseur et le dividende doivent être des types intégraux \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` et `ULong`\) pour cet opérateur.  Tous les autres types doivent d'abord être convertis en un type intégral.  L'exemple suivant illustre la division d'entier.  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Le modulo arithmétique est effectué par l'[Mod, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md).  Cet opérateur retourne le reste après que le diviseur est divisé par le dividende un nombre intégral de fois.  Si le diviseur et le dividende sont des types intégraux, la valeur retournée est un intégral.  Si le diviseur et le dividende sont des types à virgule flottante, la valeur retournée est également à virgule flottante.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### Essai de division par zéro  
 La division par zéro produit divers résultats selon les types de données impliquées.  Dans les divisions intégrales \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`\), [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] lève une exception <xref:System.DivideByZeroException>.  Dans les opérations de division sur `Decimal` ou le type de données `Single`, [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] lève également une exception <xref:System.DivideByZeroException>.  
  
 Dans les divisions à virgule flottante qui impliquent le type de données `Double`, aucune exception n'est levée, et le résultat est le membre de la classe qui représente <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>, selon le dividende.  Le tableau suivant résume les divers résultats lors d'une tentative de division d'une valeur `Double` par zéro.  
  
|||||  
|-|-|-|-|  
|Type de données d'un dividende|Type de données d'un diviseur|Valeur du dividende|Résultat|  
|`Double`|`Double`|0|<xref:System.Double.NaN> \(pas un nombre défini mathématiquement\)|  
|`Double`|`Double`|\> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Lorsque vous interceptez une exception <xref:System.DivideByZeroException>, vous pouvez utiliser ses membres pour faciliter sa gestion.  Par exemple, la propriété <xref:System.Exception.Message%2A> gère le texte du message pour l'exception.  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Opérations de décalage de bits  
 Une opération de décalage de bits effectue un décalage arithmétique sur un modèle binaire.  Ce modèle figure dans l'opérande de gauche, alors que l'opérande de droite indique le nombre de positions de décalage du modèle.  Vous pouvez décaler le modèle vers la droite à l'aide de l'[\>\> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou vers la gauche à l'aide de l'[\<\< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Le type de données de l'opérande de modèle doit être `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`.  Le type de données de l'opérande de décalage doit être `Integer` ou doit s'étendre à `Integer`.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l'autre extrémité.  Les positions binaires libérées par un décalage sont définies comme suit :  
  
-   0 pour un décalage arithmétique vers la gauche ;  
  
-   0 pour le décalage arithmétique vers la droite d'un nombre positif ;  
  
-   0 pour le décalage arithmétique vers la droite d'un type de données non signé \(`Byte`, `UShort`, `UInteger`, `ULong`\) ;  
  
-   1 pour le décalage arithmétique vers la droite d'un nombre négatif \(`SByte`, `Short`, `Integer` ou `Long`\).  
  
 L'exemple suivant décale une valeur `Integer` vers la gauche et vers la droite.  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Les décalages arithmétiques ne génèrent jamais d'exception de dépassement de capacité.  
  
## Opérateurs de bits  
 Les opérateurs logiques `Not`, `Or`, `And` et `Xor` effectuent également des opérations de bits arithmétiques lorsqu'ils sont utilisés sur des valeurs numériques.  Pour plus d'informations, consultez « Opérations de bits » dans [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## Sécurité de type  
 Les opérandes doivent généralement être du même type.  Par exemple, si vous ajoutez une variable `Integer`, vous devez l'ajouter à une autre variable `Integer`, et vous devez également assigner le résultat à une variable de type `Integer`.  
  
 Il est recommandé d'utiliser [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) pour assurer un codage correct de type sécurisé.  Si vous définissez `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] exécute automatiquement des conversions *de type sécurisé*.  Par exemple, si vous essayez d'ajouter une variable `Integer` à une variable `Double` et d'assigner la valeur à une variable `Double`, l'opération continue normalement, parce qu'une valeur `Integer` peut être convertie en `Double` sans perte de données.  En revanche, les conversions de type non sécurisé provoquent une erreur de compilation avec `Option Strict On`.  Par exemple, si vous tentez d'ajouter une variable `Integer` à une variable `Double` et d'assigner la valeur à une variable `Integer`, une erreur de compilation se produit, car une variable `Double` ne peut pas être implicitement convertie en type `Integer`.  
  
 Toutefois, si vous définissez `Option Strict Off`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] permet les conversions restrictives implicites, même si elles peuvent entraîner la perte inattendue de données ou de précision.  C'est la raison pour laquelle nous vous recommandons d'utiliser `Option Strict On` lors de l'écriture du code de production.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## Voir aussi  
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Bit Shift Operators](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)