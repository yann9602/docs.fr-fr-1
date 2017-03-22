---
title: "Comment : appeler une procédure d’opérateur (Visual Basic) | Documents Microsoft"
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
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
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
ms.openlocfilehash: 2403e7a8270c17a8db5417cd8394fd47c373d493
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Comment : appeler une procédure d'opérateur (Visual Basic)
Vous appelez une procédure d’opérateur en utilisant le symbole d’opérateur dans une expression. Dans le cas d’un opérateur de conversion, vous appelez le [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) pour convertir une valeur d’un type de données à un autre.  
  
 Vous n’appelez pas explicitement de procédures d’opérateur. Vous utilisez l’opérateur, ou la `CType` fonction, dans une instruction d’assignation ou une expression, de la même façon que vous utilisez normalement un opérateur. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]effectue l’appel à la procédure d’opérateur.  
  
 Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.  
  
### <a name="to-call-an-operator-procedure"></a>Pour appeler une procédure d’opérateur  
  
1.  Utilisez le symbole d’opérateur dans une expression de la façon habituelle.  
  
2.  Assurez-vous que les types de données des opérandes sont appropriés pour l’opérateur et dans l’ordre correct.  
  
3.  L’opérateur contribue à la valeur de l’expression comme prévu.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Pour appeler une procédure d’opérateur de conversion  
  
1.  Utilisez `CType` à l’intérieur d’une expression.  
  
2.  Assurez-vous que les types de données des opérandes sont appropriés pour la conversion et dans l’ordre correct.  
  
3.  `CType`appelle la procédure d’opérateur de conversion et retourne la valeur convertie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée deux <xref:System.TimeSpan>structures, les additionne et stocke le résultat dans une troisième <xref:System.TimeSpan>structure.</xref:System.TimeSpan> </xref:System.TimeSpan> Le <xref:System.TimeSpan>structure définit des procédures d’opérateur pour surcharger plusieurs opérateurs standards.</xref:System.TimeSpan>  
  
 [!code-vb[VbVbcnProcedures&#29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Étant donné que <xref:System.TimeSpan>surcharges de la norme `+` (opérateur), l’exemple précédent appelle une procédure d’opérateur lorsqu’il calcule la valeur de `combinedSpan`.</xref:System.TimeSpan>  
  
 Pour obtenir un exemple de l’appel de procédure d’opérateur de conversation, consultez [Comment : utiliser une classe qui définit les opérateurs](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Assurez-vous que la classe ou structure que vous utilisez définit l’opérateur que vous souhaitez utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures d’opérateur](./operator-procedures.md)   
 [Comment : définir un opérateur](./how-to-define-an-operator.md)   
 [Comment : définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md)   
 [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Conversions étendues](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Restrictives](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Comment : déclarer une Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
