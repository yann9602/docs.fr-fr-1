---
title: "- Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Negate"
  - "vb.-"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "- operator [Visual Basic]"
  - "operators [Visual Basic], subtraction"
  - "operators [Visual Basic], difference"
  - "negation operator"
  - "operators [Visual Basic], arithmetic"
  - "subtraction operator, syntax"
  - "arithmetic operators, subtraction"
  - "difference operator"
  - "math operators"
  - "operators [Visual Basic], negation"
  - "minus operator [Visual Basic]"
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# - Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Retourne la différence entre deux expressions numériques ou la valeur négative d'une expression numérique.  
  
## Syntaxe  
  
```  
  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## Composants  
 `expression1`  
 Obligatoire.  Toute expression numérique.  
  
 `expression2`  
 Requis sauf si l'opérateur `–` calcule une valeur négative.  Toute expression numérique.  
  
## Résultat  
 Le résultat constitue la différence entre `expression1` et `expression2` ou la valeur de négation de `expression1`.  
  
 Le type de données de résultat est un type numérique approprié aux types de données de `expression1` et `expression2`.  Consultez les tableaux « Arithmétique sur les entiers » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## Types pris en charge  
 Tous les types numériques.  Cela inclut les types non signés et à virgule flottante et `Decimal`.  
  
## Notes  
 Dans la première utilisation indiquée dans la syntaxe précédente, l'opérateur `–` est l'opérateur de soustraction arithmétique *binaire* permettant d'obtenir la différence entre deux expressions numériques.  
  
 Dans la seconde utilisation indiquée dans la syntaxe précédente, l'opérateur `–` est l'opérateur de négation *unaire* permettant d'obtenir la valeur négative d'une expression.  Dans ce sens, la négation consiste à inverser le signe de `expression1` ; le résultat est donc positif si `expression1` est négatif.  
  
 Si l'une ou l'autre expression a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), l'opérateur `–` la considère comme un zéro.  
  
> [!NOTE]
>  L'opérateur `–` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `–` pour calculer et retourner la différence entre deux nombres, puis pour rendre un nombre négatif.  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 Suivant l'exécution de ces instructions, `binaryResult` contient 124,45 et `unaryResult` contient \-334,90.  
  
## Voir aussi  
 [\-\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)