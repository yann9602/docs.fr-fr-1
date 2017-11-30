---
title: "^, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^, opérateur (Visual Basic)
Élève un nombre à la puissance d’un autre nombre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Composants  
 `number`  
 Obligatoire. Toute expression numérique.  
  
 `exponent`  
 Obligatoire. Toute expression numérique.  
  
## <a name="result"></a>Résultat  
 Le résultat est `number` à la puissance de `exponent`, toujours comme un `Double` valeur.  
  
## <a name="supported-types"></a>Types pris en charge  
 `Double`. Les opérandes de tous types sont convertis en `Double`.  
  
## <a name="remarks"></a>Remarques  
 Visual Basic exécute toujours l’élévation à la puissance de la [Type de données Double](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 La valeur de `exponent` peut être fractionnaire, négative, ou les deux.  
  
 Lorsque plusieurs élévation est effectuée dans une expression unique, la `^` opérateur est évalué comme il est rencontré, de gauche à droite.  
  
> [!NOTE]
>  Le `^` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `^` opérateur pour élever un nombre à la puissance d’un exposant. Le résultat est le premier opérande élevé à la puissance de la seconde.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 L’exemple précédent génère les résultats suivants :  
  
 `exp1`a la valeur 4 (2 au carré).  
  
 `exp2`a la valeur 19 683 (3 au cube, puis cette valeur au cube).  
  
 `exp3`a la valeur-125 (-5 au cube).  
  
 `exp4`a la valeur 625 (-5 à la puissance quatre).  
  
 `exp5`a la valeur 2 (racine cubique de 8).  
  
 `exp6`a la valeur 0,5 (1,0 divisé par la racine cubique de 8).  
  
 Notez l’importance des parenthèses dans les expressions dans l’exemple précédent. Raison de *la priorité des opérateurs*, Visual Basic exécute normalement le `^` opérateur avant les autres, même l’unaire `–` opérateur. Si `exp4` et `exp6` avaient été calculés sans parenthèses, ils aurait produit les résultats suivants :  
  
 `exp4 = -5 ^ 4`serait calculé comme-(5 à la puissance quatre), ce qui entraînerait-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0`serait calculé comme (8 à la puissance-1, ou 0,125) divisé par 3,0, ce qui donnerait 0,041666666666666666666666666666667.  
  
## <a name="see-also"></a>Voir aussi  
 [^= (opérateur)](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
