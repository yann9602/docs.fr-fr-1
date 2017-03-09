---
title: "^ Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.^"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising numbers to powers"
  - "^ operator [Visual Basic], exponention"
  - "square operator"
  - "^ operator [Visual Basic]"
  - "exponentiation operator [Visual Basic]"
  - "exponent"
  - "numbers, rasing"
  - "powers"
  - "arithmetic operators, exponentiation"
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# ^ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Élève un nombre à la puissance d'un autre nombre.  
  
## Syntaxe  
  
```  
  
number ^ exponent  
```  
  
## Composants  
 `number`  
 Obligatoire.  Toute expression numérique.  
  
 `exponent`  
 Obligatoire.  Toute expression numérique.  
  
## Résultat  
 Le résultat est `number` élevé à la puissance `exponent`, toujours comme une valeur `Double`.  
  
## Types pris en charge  
 `Double`.  Les opérandes de tous types sont convertis en `Double`.  
  
## Notes  
 Visual Basic exécute toujours l'élévation à la puissance dans le [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 La valeur de `exponent` peut être fractionnaire, négative ou les deux.  
  
 Lorsque plusieurs élévations à la puissance sont effectuées dans une même expression, l'opérateur `^` est évalué à mesure qu'il est rencontré, de gauche à droite.  
  
> [!NOTE]
>  L'opérateur `^` peut être *surchargé*, ce qui signifie qu'une classe ou une structure peut redéfinir son comportement lorsqu'un opérande a le type de cette classe ou de cette structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `^` pour élever un nombre à la puissance d'un exposant.  Le résultat est le premier opérande élevé à la puissance de la deuxième.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/exponentiation-operator_1.vb)]  
  
 L'exemple précédent donne les résultats suivants :  
  
 `exp1` a la valeur 4 \(2 au carré\).  
  
 `exp2` a la valeur 19 683 \(3 au cube, puis cette valeur au cube\).  
  
 `exp3` a la valeur \-125 \(\-5 au cube\).  
  
 `exp4` a la valeur 625 \(\-5 à la puissance quatre\).  
  
 `exp5` a la valeur 2 \(racine cubique de 8\).  
  
 `exp6` a la valeur 0,5 \(1,0 divisé par la racine cubique de 8\).  
  
 Notez l'importance des parenthèses dans les expressions de l'exemple précédent.  À cause de la *priorité des opérateurs*, Visual Basic exécute normalement l'opérateur `^` avant tous les autres, même l'opérateur unaire `–`.  Si `exp4` et `exp6` avaient été calculés sans parenthèses, le résultat obtenu serait le suivant :  
  
 `exp4 = -5 ^ 4` est calculé comme – \(5 à la quatrième puissance\), qui entraînerait \-625.  
  
 `exp6 = 8 ^ -1.0 / 3.0` serait calculé comme \(8 à la puissance \-1, ou 0,125\) divisé par 3,0, ce qui donnerait 0,041666666666666666666666666666667.  
  
## Voir aussi  
 [^\= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)