---
title: "&amp;Opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a>&amp;Opérateur (Visual Basic)
Génère une concaténation de chaîne de deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. N’importe quel `String` ou `Object` variable.  
  
 `expression1`  
 Obligatoire. Toute expression avec un type de données qui s’étend à `String`.  
  
 `expression2`  
 Obligatoire. Toute expression avec un type de données qui s’étend à `String`.  
  
## <a name="remarks"></a>Remarques  
 Si le type de données de `expression1` ou `expression2` n’est pas `String` mais s’étend à `String`, il est converti en `String`. Si un des types de données ne s’étend pas à `String`, le compilateur génère une erreur.  
  
 Type de données de `result` est `String`. Si un ou les deux expressions ont [rien](../../../visual-basic/language-reference/nothing.md) ou avoir la valeur <xref:System.DBNull.Value?displayProperty=nameWithType>, elles sont traitées comme une chaîne avec la valeur « ».  
  
> [!NOTE]
>  Le `&` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  Le caractère esperluette (&) peuvent également servir à identifier des variables en tant que type `Long`. Pour plus d’informations, consultez [caractères de Type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `&` opérateur pour forcer la concaténation de chaîne. Le résultat est une valeur de chaîne représentant la concaténation de deux opérandes de chaîne.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [&= (opérateur)](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs de concaténation dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
