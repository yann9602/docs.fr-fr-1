---
title: "And, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a>And, opérateur (Visual Basic)
Effectue une conjonction logique sur deux `Boolean` expressions ou conjonction au niveau du bit sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. N’importe quel `Boolean` ou expression numérique. Pour la comparaison Boolean, `result` est la conjonction logique de deux `Boolean` valeurs. Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. N’importe quel `Boolean` ou expression numérique.  
  
 `expression2`  
 Obligatoire. N’importe quel `Boolean` ou expression numérique.  
  
## <a name="remarks"></a>Remarques  
 Pour la comparaison Boolean, `result` est `True` si et seulement si `expression1` et `expression2` correspondre à `True`. Le tableau suivant illustre comment `result` est déterminée.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Dans la comparaison Boolean, le `And` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. Le [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *de court-circuit*, ce qui signifie que si `expression1` est `False`, puis `expression2` n’est pas évaluée.  
  
 Quand il est appliqué à des valeurs numériques, la `And` opérateur effectue une comparaison au niveau du bit de position identique dans deux expressions numériques et définit le bit dans correspondant `result` conformément au tableau suivant.  
  
|Si bit dans `expression1` est|Et que le bit de `expression2` est|Le bit `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations de bits doivent être placées entre parenthèses pour garantir des résultats précis.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une `Boolean` expression et une expression numérique, Visual Basic convertit le `Boolean` expression à une valeur numérique (-1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.  
  
 Pour une comparaison Boolean, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez le tableau « Relationnelles et au niveau du bit des comparaisons » [Types de données de résultats de l’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  Le `And` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `And` opérateur effectue une conjonction logique sur deux expressions. Le résultat est un `Boolean` valeur qui indique si les deux expressions sont `True`.  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 L’exemple précédent produit des résultats de `True` et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `And` opérateur pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques. Le bit du modèle de résultat est défini si les bits correspondants dans les opérandes sont toutes deux définies sur 1.  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 L’exemple précédent produit des résultats de 8, 2 et 0, respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [AndAlso (opérateur)](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
