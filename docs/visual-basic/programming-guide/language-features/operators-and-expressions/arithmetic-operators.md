---
title: "Opérateurs arithmétiques en Visual Basic | Documents Microsoft"
ms.custom: 
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
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators
- bit-shift operators
- zero, division by zero
- operators [Visual Basic], arithmetic
- division, by zero
- Visual Basic code, operators
- arithmetic operators, about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
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
ms.openlocfilehash: c724bf8b6794e71d49b32c7d3ce9e010f541f68f
ms.lasthandoff: 03/13/2017

---
# <a name="arithmetic-operators-in-visual-basic"></a>Opérateurs arithmétiques en Visual Basic
Opérateurs arithmétiques sont utilisés pour effectuer de nombreuses opérations arithmétiques familières qui impliquent le calcul de valeurs numériques représentées par des littéraux, variables, autres expressions, fonction appels de propriété et des constantes. Également classés avec les opérateurs arithmétiques sont les opérateurs de décalage de bits, qui agissent au niveau des bits des opérandes individuels et leurs modèles de bits de décalage vers la gauche ou la droite.  
  
## <a name="arithmetic-operations"></a>Opérations arithmétiques  
 Vous pouvez ajouter deux valeurs dans une expression avec la [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md), ou soustraire une valeur d’une autre avec les [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators&#57;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Négation utilise également le [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mais avec un seul opérande, comme l’exemple suivant montre comment.  
  
 [!code-vb[VbVbalrOperators&#58;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Multiplication et division utilisent le [* opérateur](../../../../visual-basic/language-reference/operators/multiplication-operator.md) et [/, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivement, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators&#59;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Élévation à la puissance utilise le [^ opérateur](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators&#60;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Division d’entier s’effectue à l’aide de la [\, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Division d’entier retourne le quotient, autrement dit, l’entier qui représente le nombre de fois où le diviseur peut être divisé par le dividende sans tenir compte du reste. Le diviseur et le dividende doivent être des types intégrés (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, et `ULong`) pour cet opérateur. Tous les autres types doivent tout d’abord être convertis en un type intégral. L’exemple suivant illustre la division d’entier.  
  
 [!code-vb[VbVbalrOperators&#61;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Modulo arithmétique est effectué à l’aide de la [Mod, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md). Cet opérateur retourne le reste après que le diviseur par le dividende un nombre intégral de fois. Si le diviseur et le dividende sont des types intégraux, la valeur retournée est intégrale. Si le diviseur et le dividende sont des types à virgule flottante, la valeur retournée est également à virgule flottante. L’exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators&#62;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators&#63;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Division par zéro produit des résultats différents selon les types de données impliqués. In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</xref:System.DivideByZeroException> Dans les opérations de division sur la `Decimal` ou `Single` type de données, le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] lève également une <xref:System.DivideByZeroException>exception.</xref:System.DivideByZeroException>  
  
 Dans les divisions à virgule flottante qui implique le `Double` type de données, aucune exception n’est levée et le résultat est le membre de classe représentant <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, ou <xref:System.Double.NegativeInfinity>, selon le dividende.</xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.Double.NaN> Le tableau suivant résume les différents résultats de la tentative de diviser un `Double` valeur par zéro.  
  
|Type de données dividende|Type de données diviseur|Valeur du dividende|Résultat|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(pas un nombre défini mathématiquement)</xref:System.Double.NaN>|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity></xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity></xref:System.Double.NegativeInfinity>|  
  
 Lorsque vous interceptez une <xref:System.DivideByZeroException>qu'exception, vous pouvez utiliser ses membres pour vous aider à gérer celui-ci.</xref:System.DivideByZeroException> Par exemple, le <xref:System.Exception.Message%2A>propriété contient le texte du message pour l’exception.</xref:System.Exception.Message%2A> Pour plus d’informations, consultez [essayez... Catch... Instruction finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Opérations de décalage de bits  
 Une opération de décalage de bits effectue un décalage arithmétique sur un modèle binaire. Le modèle est contenu dans l’opérande de gauche, tandis que l’opérande de droite indique le nombre de positions pour décaler le modèle. Vous pouvez décaler le modèle vers la droite avec le [>> opérateur](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou vers la gauche avec la [ <> </> ](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Le type de données de l’opérande de modèle doit être `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`. Le type de données de l’opérande de décalage doit être `Integer` ou doit s’étendre à `Integer`.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Les positions de bit libérées par un décalage sont définies comme suit :  
  
-   0 pour un décalage arithmétique vers la gauche  
  
-   0 pour un décalage arithmétique vers la droite d’un nombre positif  
  
-   0 pour un décalage arithmétique vers la droite d’un type de données non signé (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   1 pour un décalage arithmétique vers la droite d’un nombre négatif (`SByte`, `Short`, `Integer`, ou `Long`)  
  
 L’exemple suivant Décale une `Integer` valeur gauche et droite.  
  
 [!code-vb[VbVbalrOperators&#64;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Les décalages arithmétiques ne génèrent jamais des exceptions de dépassement de capacité.  
  
## <a name="bitwise-operations"></a>Opérations de bits  
 Opérateurs logiques, `Not`, `Or`, `And`, et `Xor` également effectuer les opérations de bits arithmétiques lorsqu’ils sont utilisés sur des valeurs numériques. Pour plus d’informations, consultez « Opérations de bits » dans [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Sécurité de type  
 Opérandes doivent généralement être du même type. Par exemple, si vous ajoutez avec une `Integer` variable, vous devez l’ajouter à un autre `Integer` variable et vous devez attribuer le résultat à une variable de type `Integer` également.  
  
 Pour assurer le bon type-safe pratique de programmation consiste à utiliser le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Si vous définissez `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] effectue automatiquement *type-safe* conversions. Par exemple, si vous essayez d’ajouter un `Integer` à la variable un `Double` variable et attribuez la valeur à un `Double` variable, l’opération continue normalement, parce qu’un `Integer` valeur peut être convertie en `Double` sans perte de données. Conversions de type sécurisé en revanche, le compilateur génère une erreur avec `Option Strict On`. Par exemple, si vous essayez d’ajouter un `Integer` à la variable un `Double` variable et attribuez la valeur à une `Integer` variable, une erreur de compilation se produit, car un `Double` variable ne peut pas être convertie implicitement en type `Integer`.  
  
 Si vous définissez `Option Strict Off`, toutefois, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permet les conversions restrictives implicites, même si elles peuvent entraîner une perte inattendue de données ou de précision. Pour cette raison, nous vous recommandons d’utiliser `Option Strict On` lors de l’écriture de code de production. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Opérateurs de décalage de bits](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
