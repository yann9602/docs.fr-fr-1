---
title: "/ Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb./"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, floating point"
  - "floating-point numbers, division operator"
  - "slash (/) operator"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "arithmetic operators, division"
  - "division, by zero"
  - "operators [Visual Basic], division"
  - "division operator, syntax"
  - "/ operator [Visual Basic]"
  - "math operators"
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# / Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Effectue la division entre deux nombres et retourne un résultat à virgule flottante.  
  
## Syntaxe  
  
```  
  
expression1 / expression2  
```  
  
## Composants  
 `expression1`  
 Obligatoire.  Toute expression numérique.  
  
 `expression2`  
 Obligatoire.  Toute expression numérique.  
  
## Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, ainsi que `Decimal`.  
  
## Résultat  
 Le résultat correspond au quotient entier de `expression1` divisé par `expression2`, y compris tout élément restant.  
  
 Le [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) retourne le quotient entier, sans le reste.  
  
## Notes  
 Le type de données du résultat dépend du type des opérandes.  Le tableau suivant montre la façon dont le type de données du résultat est déterminé.  
  
|Types de données d'opérande|Type de données du résultat|  
|---------------------------------|---------------------------------|  
|Les deux expressions sont des types de données intégraux \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\)|`Double`|  
|Une expression est un type de données [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) et l'autre n'est pas un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md).|`Single`|  
|Une expression est un type de données [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) et l'autre n'est pas [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|L'une ou l'autre expression est un type de données [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
  
 Avant d'effectuer la division, toutes les expressions numériques intégrales sont étendues à `Double`.  Si vous assignez le résultat à un type de données intégral, Visual Basic essaie de convertir le résultat de `Double` en type de données intégral.  Cela peut lever une exception si le résultat ne correspond pas à ce type de données.  Consultez en particulier « Essai de division par Zéro » sur cette page de l'aide.  
  
 Si `expression1` ou `expression2` correspond à [Nothing](../../../visual-basic/language-reference/nothing.md), elle est considérée comme un zéro.  
  
## Essai de division par zéro  
 Si la valeur de `expression2` est zéro, l'opérateur `/` se comporte différemment pour les divers types de données d'opérande.  Le tableau suivant répertorie les comportements possibles.  
  
|Types de données d'opérande|Comportement si la valeur de `expression2` est zéro|  
|---------------------------------|---------------------------------------------------------|  
|Virgule flottante \(`Single` ou `Double`\)|Retourne un nombre infini \(<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>\), ou <xref:System.Double.NaN> \(pas un nombre\) si la valeur de `expression1` est également zéro|  
|`Decimal`|Lève <xref:System.DivideByZeroException>|  
|Intégral \(signé ou non signé\)|Toute tentative de conversion en type intégral lève une exception <xref:System.OverflowException>, car les types intégraux ne peuvent pas accepter <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity> ou <xref:System.Double.NaN>|  
  
> [!NOTE]
>  L'opérateur `/` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple utilise l'opérateur `/` pour effectuer une division à virgule flottante.  Le résultat est le quotient des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Les expressions de l'exemple précédent retournent les valeurs 2,5 et 3,333333.  Notez que le résultat possède toujours une virgule flottante \(`Double`\), bien que les deux opérandes soient des constantes entières.  
  
## Voir aussi  
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)