---
title: "- Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
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
ms.openlocfilehash: 7f45094da7bc61687d9c767d25858aa214bf1978
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>-, opérateur (Visual Basic)
Retourne la différence entre deux expressions numériques ou la valeur négative d’une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>Composants  
 `expression1`  
 Obligatoire. Toute expression numérique.  
  
 `expression2`  
 Requis sauf si la `–` opérateur calcule une valeur négative. Toute expression numérique.  
  
## <a name="result"></a>Résultat  
 Le résultat est la différence entre `expression1` et `expression2`, ou la valeur négative de `expression1`.  
  
 Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez les tableaux « Arithmétique sur les entiers » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques. Cela inclut les types non signés et à virgule flottante et `Decimal`.  
  
## <a name="remarks"></a>Notes  
 Dans la première utilisation indiquée dans la syntaxe précédente, le `–` opérateur est la *binaire* opérateur de soustraction arithmétique de la différence entre deux expressions numériques.  
  
 Dans la seconde utilisation indiquée dans la syntaxe précédente, le `–` opérateur est la *unaire* opérateur de négation de la valeur négative d’une expression. Dans ce sens, la négation consiste à inverser le signe de `expression1` afin que le résultat est positif si `expression1` est négatif.  
  
 Si des expressions a la valeur [rien](../../../visual-basic/language-reference/nothing.md), le `–` opérateur considère comme un zéro.  
  
> [!NOTE]
>  Le `–` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `–` opérateur pour calculer et retourner la différence entre deux nombres, puis pour rendre un nombre négatif.  
  
 [!code-vb[VbVbalrOperators&#10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Après l’exécution de ces instructions, `binaryResult` contient 124,45 et `unaryResult` contient -334,90.  
  
## <a name="see-also"></a>Voir aussi  
 [-=, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [des opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

