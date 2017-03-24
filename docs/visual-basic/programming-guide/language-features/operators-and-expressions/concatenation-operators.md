---
title: "Opérateurs de concaténation dans Visual Basic | Documents Microsoft"
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
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
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
ms.openlocfilehash: fa11f1dcff2c333861596cbac03391403cf962c1
ms.lasthandoff: 03/13/2017

---
# <a name="concatenation-operators-in-visual-basic"></a>Opérateurs de concaténation (Visual Basic)
Les opérateurs de concaténation joignent plusieurs chaînes en une seule. Il existe deux opérateurs de concaténation, `+` et `&`. Les deux effectuent l'opération de concaténation de base, comme le montre l'exemple suivant.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Ces opérateurs peuvent également concaténer les variables `String`, comme illustré ici.  
  
 [!code-vb[VbVbalrOperators&#76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Différences entre ces deux opérateurs de concaténation  
 Le [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md) a pour objectif principal d’ajouter deux nombres. Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne. Le `+` opérateur comporte un ensemble complexe de règles qui déterminent s’il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exécution <xref:System.InvalidCastException>exception.</xref:System.InvalidCastException>  
  
 Le [s’opérateur](../../../../visual-basic/language-reference/operators/concatenation-operator.md) est défini uniquement pour `String` opérandes et il étend toujours ses opérandes à `String`, quelle que soit la valeur de `Option Strict`. L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.  
  
## <a name="performance-string-and-stringbuilder"></a>Performance : String et StringBuilder  
 Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, des suppressions et des remplacements, vos performances peuvent tirer profit de la <xref:System.Text.StringBuilder>classe dans le <xref:System.Text>espace de noms.</xref:System.Text> </xref:System.Text.StringBuilder> Elle prend une instruction supplémentaire pour créer et initialiser un <xref:System.Text.StringBuilder>objet et une autre instruction pour convertir sa valeur finale à un `String`, mais vous pouvez effectuer une récupération parce que <xref:System.Text.StringBuilder>peut s’exécuter plus rapidement.</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder>  
  
## <a name="see-also"></a>Voir aussi  
 [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Types de méthodes de Manipulation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
