---
title: "\\, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38718b109b4b3865238267039908ea1d51d06229
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>\, opérateur (Visual Basic)
Divise deux nombres et retourne un résultat entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Composants  
 `expression1`  
 Obligatoire. Toute expression numérique.  
  
 `expression2`  
 Obligatoire. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante et `Decimal`.  
  
## <a name="result"></a>Résultat  
 Le résultat est le quotient entier de `expression1` divisé par `expression2`, qui abandonne tout reste et conserve uniquement la partie entière. Il s’agit en tant que *troncation*.  
  
 Le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`. Consultez les tableaux « Arithmétique sur les entiers » dans [Types de données de résultats de l’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) renvoie le quotient complet qui conserve le reste dans la partie fractionnaire.  
  
## <a name="remarks"></a>Remarques  
 Avant d’effectuer la division, Visual Basic essaie de convertir n’importe quelle expression numérique à virgule flottante `Long`. Si `Option Strict` est `On`, une erreur de compilation se produit. Si `Option Strict` est `Off`, un <xref:System.OverflowException> est possible que si la valeur est en dehors de la plage de la [Type de données Long](../../../visual-basic/language-reference/data-types/long-data-type.md). La conversion en `Long` est également soumis à *l’arrondi bancaire*. Pour plus d’informations, consultez « Parties fractionnaires » dans [les fonctions de Conversion de Type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Si `expression1` ou `expression2` prend la valeur de [rien](../../../visual-basic/language-reference/nothing.md), il est traité en tant que zéro.  
  
## <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Si `expression2` correspond à zéro, le `\` opérateur lève une <xref:System.DivideByZeroException> exception. Cela est vrai pour tous les types de données numériques des opérandes.  
  
> [!NOTE]
>  Le `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `\` opérateur effectue la division d’entier. Le résultat est un entier qui représente le quotient entier des deux opérandes avec le reste abandonné.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 Les expressions dans l’exemple précédent retournent les valeurs de 2, 3, 33 et -22, respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
