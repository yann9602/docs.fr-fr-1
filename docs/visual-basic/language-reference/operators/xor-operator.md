---
title: "Xor, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a>Xor, opérateur (Visual Basic)
Effectue une exclusion logique sur deux `Boolean` expressions ou une exclusion au niveau du bit sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. N’importe quel `Boolean` ou une variable numérique. Pour la comparaison Boolean, `result` est l’exclusion logique (disjonction logique exclusive) de deux `Boolean` valeurs. Pour les opérations au niveau du bit, `result` est une valeur numérique qui représente l’exclusion de bits (disjonction d’opérations de bits exclusive) de deux modèles binaires numériques.  
  
 `expression1`  
 Obligatoire. N’importe quel `Boolean` ou expression numérique.  
  
 `expression2`  
 Obligatoire. N’importe quel `Boolean` ou expression numérique.  
  
## <a name="remarks"></a>Remarques  
 Pour la comparaison Boolean, `result` est `True` si et seulement si un seul de `expression1` et `expression2` prend la valeur `True`. Autrement dit, si et seulement si `expression1` et `expression2` évaluer opposé à `Boolean` valeurs. Le tableau suivant illustre comment `result` est déterminée.  
  
|Si `expression1` est|Et `expression2` est|La valeur de `result` est|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Dans la comparaison Boolean, le `Xor` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure. Il n’existe pas d’équivalent court-circuit `Xor`, car le résultat dépend toujours des deux opérandes. Pour *de court-circuit* des opérateurs logiques, consultez [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) et [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Pour les opérations au niveau du bit, le `Xor` opérateur effectue une comparaison au niveau du bit de position identique dans deux expressions numériques et définit le bit dans correspondant `result` conformément au tableau suivant.  
  
|Si bit dans `expression1` est|Et que le bit de `expression2` est|Le bit `result` est|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des opérateurs arithmétiques et relationnels, toutes les opérations de bits doivent être placées entre parenthèses pour garantir une exécution précise.  
  
 Par exemple, 5 `Xor` 3 est 6. Pour voir pourquoi il s’agit, convertissez 5 et 3 en leurs représentations binaire, 101 et 011. Puis utilisez le tableau précédent pour déterminer que 101 Xor 011 est 110, la représentation binaire du nombre décimal 6.  
  
## <a name="data-types"></a>Types de données  
 Si les opérandes se composent d’une `Boolean` expression et une expression numérique, Visual Basic convertit le `Boolean` expression à une valeur numérique (-1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.  
  
 Pour un `Boolean` comparaison, le type de données du résultat est `Boolean`. Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez le tableau « Relationnelles et au niveau du bit des comparaisons » [Types de données de résultats de l’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Surcharge  
 Le `Xor` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Xor` opérateur pour effectuer une exclusion logique (disjonction logique exclusive) sur deux expressions. Le résultat est un `Boolean` valeur qui indique si un seul des expressions est `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 L’exemple précédent produit des résultats de `False`, `True`, et `False`, respectivement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Xor` opérateur pour effectuer une exclusion logique (disjonction logique exclusive) sur les bits individuels de deux expressions numériques. Le bit du modèle de résultat est défini si un seul des bits correspondants dans les opérandes a la valeur 1.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 L’exemple précédent produit les résultats de 2, 12 et 14, respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques/de bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs logiques et au niveau du bit en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
