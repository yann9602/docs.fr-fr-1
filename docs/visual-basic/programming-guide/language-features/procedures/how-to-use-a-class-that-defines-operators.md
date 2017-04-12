---
title: "Comment : utiliser une classe qui définit des opérateurs (Visual Basic) | Documents Microsoft"
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
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: b1db7c0b2a6fd8160baa48892b5f2214df24674e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Comment : utiliser une classe qui définit des opérateurs (Visual Basic)
Si vous utilisez une classe ou structure qui définit ses propres opérateurs, vous pouvez accéder à ces opérateurs de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Définition d’un opérateur sur une classe ou structure est également appelée *surcharge* l’opérateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant accède à la structure SQL <xref:System.Data.SqlTypes.SqlString>, qui définit les opérateurs de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) dans les deux sens entre une chaîne SQL et une [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chaîne.</xref:System.Data.SqlTypes.SqlString> Utilisez `CType(` *expression de chaîne SQL*, `String)` pour convertir une chaîne SQL pour un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chaîne, et `CType(` *expression de chaîne Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` convertir dans l’autre direction.</xref:System.Data.SqlTypes.SqlString>  
  
 [!code-vb[30 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 Le <xref:System.Data.SqlTypes.SqlString>structure définit un opérateur de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md)) à partir de `String` à <xref:System.Data.SqlTypes.SqlString>et l’autre à partir de <xref:System.Data.SqlTypes.SqlString>à `String`.</xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> L’instruction qui assigne `title` à `jobTitle` utilise le premier opérateur et le <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>appel de fonction utilise le second.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Assurez-vous que la classe ou structure que vous utilisez définit l’opérateur que vous souhaitez utiliser. Ne supposez pas que la classe ou la structure a défini chaque opérateur comme disponible pour la surcharge. Pour obtenir la liste des opérateurs disponibles, consultez la page [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Inclure approprié `Imports` instruction pour la chaîne SQL au début de votre fichier source (dans ce cas <xref:System.Data.SqlTypes>).</xref:System.Data.SqlTypes>  
  
 Votre projet doit contenir des références à System.Data et System.XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures d’opérateur](./operator-procedures.md)   
 [Comment : définir un opérateur](./how-to-define-an-operator.md)   
 [Comment : définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md)   
 [Comment : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)   
 [Conversions étendues](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Restrictives](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Comment : déclarer une Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
