---
title: "Opérateurs arithmétiques en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7fec98c38eebc34a0f84e051dc7c0914f537418f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operators-in-visual-basic"></a>Opérateurs arithmétiques en Visual Basic
Opérateurs arithmétiques sont utilisés pour effectuer la plupart des opérations arithmétiques familières qui impliquent le calcul de valeurs numériques représentées par des littéraux, variables, autres expressions, fonction les appels de propriété et des constantes. Également classés avec les opérateurs arithmétiques sont les opérateurs de décalage de bits, qui agissent au niveau des bits individuels des opérandes et leurs modèles de bits est déplacée vers la gauche ou la droite.  
  
## <a name="arithmetic-operations"></a>Opérations arithmétiques  
 Vous pouvez ajouter deux valeurs dans une expression avec le [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md), ou soustraire une valeur d’une autre avec la [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Négation utilise également le [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mais avec un seul opérande, comme l’exemple suivant montre comment.  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Multiplication et division utilisent le [* opérateur](../../../../visual-basic/language-reference/operators/multiplication-operator.md) et [/, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivement, comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Élévation à la puissance utilise le [^ opérateur](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Division d’entier est effectuée à l’aide de la [\, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Division d’entier renvoie le quotient, autrement dit, l’entier qui représente le nombre de fois où le diviseur peut être divisé par le dividende sans tenir compte du reste. Le diviseur et le dividende doivent être des types intégraux (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, et `ULong`) pour cet opérateur. Tous les autres types doivent tout d’abord être convertis en un type intégral. L’exemple suivant montre la division d’entier.  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Modulo arithmétique est effectué à l’aide de la [MOD, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md). Cet opérateur retourne le reste après que le diviseur par le dividende un nombre intégral de fois. Si le diviseur et le dividende sont des types intégraux, la valeur retournée est intégral. Si le diviseur et le dividende sont des types à virgule flottante, la valeur retournée est également à virgule flottante. L’exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Une division par zéro a des résultats différents selon les types de données impliqués. Dans les divisions intégrales (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lève une <xref:System.DivideByZeroException> exception. Dans les opérations de division sur la `Decimal` ou `Single` type de données, le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lève également une <xref:System.DivideByZeroException> exception.  
  
 Unités de division à virgule flottante qui impliquent le `Double` type de données, aucune exception n’est levée et le résultat est le membre de classe représentant <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, ou <xref:System.Double.NegativeInfinity>, selon le dividende. Le tableau suivant résume les différents résultats de la tentative de diviser un `Double` valeur par zéro.  
  
|Type de données dividende|Type de données diviseur|Valeur du dividende|Résultat|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(pas un nombre défini mathématiquement)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Lorsque vous interceptez une <xref:System.DivideByZeroException> exception, vous pouvez utiliser ses membres pour vous aider à gérer. Par exemple, le <xref:System.Exception.Message%2A> propriété contient le texte du message pour l’exception. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Opérations de décalage de bits  
 Une opération de décalage de bits effectue un décalage arithmétique sur un modèle binaire. Le modèle est contenu dans l’opérande de gauche, alors que l’opérande de droite spécifie le nombre de positions pour décaler le modèle. Vous pouvez décaler le modèle vers la droite avec le [>> opérateur](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou à gauche avec la [<< opérateur](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Le type de données de l’opérande de modèle doit être `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`. Le type de données de l’opérande de décalage doit être `Integer` ou doit s’étendre au `Integer`.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Les positions binaires libérées par un décalage sont définies comme suit :  
  
-   0 pour un décalage arithmétique vers la gauche  
  
-   0 pour un décalage arithmétique vers la droite d’un nombre positif  
  
-   0 pour un décalage arithmétique vers la droite d’un type de données non signé (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   1 pour un décalage arithmétique vers la droite d’un nombre négatif (`SByte`, `Short`, `Integer`, ou `Long`)  
  
 L’exemple suivant Décale une `Integer` valeur gauche et droite.  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Les décalages arithmétiques ne génèrent jamais des exceptions de dépassement de capacité.  
  
## <a name="bitwise-operations"></a>Opérations de bits  
 En plus des opérateurs logiques `Not`, `Or`, `And`, et `Xor` également effectuer les opérations de bits arithmétiques lorsqu’il est utilisé sur des valeurs numériques. Pour plus d’informations, consultez « Opérations de bits » dans [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Sécurité de type  
 Opérandes doivent normalement être du même type. Par exemple, si vous effectuez un ajout avec un `Integer` variable, vous devez l’ajouter à un autre `Integer` variable et vous devez assigner le résultat à une variable de type `Integer` également.  
  
 Pour garantir le bon type sécurisé pratique de programmation consiste à utiliser le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Si vous définissez `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] effectue automatiquement *type sécurisé* conversions. Par exemple, si vous essayez d’ajouter un `Integer` variable à un `Double` variable et assigner la valeur à un `Double` variable, l’opération se poursuit normalement, car un `Integer` valeur peut être convertie en `Double` sans perte de données. Conversions de type sécurisé en revanche, le compilateur génère une erreur avec `Option Strict On`. Par exemple, si vous essayez d’ajouter un `Integer` variable à un `Double` variable et assigner la valeur à une `Integer` variable, une erreur du compilateur se produit, car un `Double` variable ne peut pas être implicitement convertie en type `Integer`.  
  
 Si vous définissez `Option Strict Off`, toutefois, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] permet les conversions restrictives implicites, même si elles peuvent entraîner la perte inattendue de données ou de précision. Pour cette raison, nous vous recommandons d’utiliser `Option Strict On` lors de l’écriture de code de production. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Opérateurs de décalage de bits](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
