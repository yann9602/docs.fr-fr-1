---
title: "* Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.*"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, multiplication"
  - "operators [Visual Basic], multiplication"
  - "* operator [Visual Basic]"
  - "multiplication operator, syntax"
  - "math operators"
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# * Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Multiplie deux nombres.  
  
## Syntaxe  
  
```  
  
number1 * number2  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`number1`|Obligatoire.  Toute expression numérique.|  
|`number2`|Obligatoire.  Toute expression numérique.|  
  
## Résultat  
 Le résultat est le produit de `number1` et `number2`.  
  
## Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, ainsi que `Decimal`.  
  
## Notes  
 Le type de données du résultat dépend du type des opérandes.  Le tableau suivant montre la façon dont le type de données du résultat est déterminé.  
  
|||  
|-|-|  
|Types de données d'opérande|Type de données du résultat|  
|Les deux expressions sont des types de données intégraux \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\)|Type de données numériques approprié pour les types de données de `number1` et `number2`.  Consultez les tableaux « Arithmétique sur les entiers » dans [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Les deux expressions sont [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Les deux expressions sont [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|L'une des expressions est un type de données à virgule flottante \(`Single` ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)\), mais les deux ne sont pas `Single` \(remarquez que `Decimal` n'est pas un type de données à virgule flottante\)|`Double`|  
  
 Si une expression a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), elle est considérée comme un zéro.  
  
## Surcharge  
 L'opérateur `*` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 Cet exemple utilise l'opérateur `*` pour multiplier deux nombres.  Le résultat est le produit des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## Voir aussi  
 [\*\= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)