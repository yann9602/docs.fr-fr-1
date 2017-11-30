---
title: "Mod, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a>Mod, opérateur (Visual Basic)
Divise deux nombres et retourne uniquement le reste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>Composants  
 `number1`  
 Obligatoire. Toute expression numérique.  
  
 `number2`  
 Obligatoire. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques. Cela inclut les types non signés et à virgule flottante et `Decimal`.  
  
## <a name="result"></a>Résultat  
 Le résultat est le reste après `number1` divisé par `number2`. Par exemple, l’expression `14 Mod 4` prend la valeur 2.  
  
## <a name="remarks"></a>Remarques  
 Si le paramètre `number1` ou `number2` est une valeur à virgule flottante, le reste à virgule flottante de la division est retourné. Le type de données du résultat est le plus petit type de données qui peut contenir toutes les valeurs possibles qui résultent de la division avec les types de données de `number1` et `number2`.  
  
 Si `number1` ou `number2` prend la valeur de [rien](../../../visual-basic/language-reference/nothing.md), il est traité en tant que zéro.  
  
 Les opérateurs connexes sont les suivantes :  
  
-   Le [\, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) renvoie le quotient entier d’une division. Par exemple, l’expression `14 \ 4` renvoie la valeur 3.  
  
-   Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retourne le quotient complet, y compris le reste, en tant que nombre à virgule flottante. Par exemple, l’expression `14 / 4` prend la valeur 3,5.  
  
## <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Si `number2` correspond à zéro, le comportement de la `Mod` opérateur varie selon le type de données des opérandes. Une division intégrale lève une <xref:System.DivideByZeroException> exception. Une division à virgule flottante retourne <xref:System.Double.NaN>.  
  
## <a name="equivalent-formula"></a>Formule équivalente  
 L’expression `a Mod b` correspond à une des formules suivantes :  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>À virgule flottante imprécision  
 Lorsque vous travaillez avec des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours de représentation précise dans la mémoire. Cela peut entraîner des résultats inattendus à partir de certaines opérations, telles que la comparaison de valeurs et les `Mod` opérateur. Pour plus d’informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="overloading"></a>Surcharge  
 Le `Mod` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement. Si votre code applique `Mod` à une instance d’une classe ou une structure qui inclut une telle surcharge, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Mod` opérateur diviser deux nombres et retourner uniquement le reste. Si un nombre est un nombre à virgule flottante, le résultat est un nombre à virgule flottante qui représente le reste.  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’imprécision potentielle des opérandes à virgule flottante. Dans la première instruction, les opérandes sont `Double`, et 0,2 représente une fraction binaire se répétant avec une valeur stockée de 0,20000000000000001. Dans la deuxième instruction, le littéral de type caractère `D` force les deux opérandes de `Decimal`, et 0,2 a une représentation précise.  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
