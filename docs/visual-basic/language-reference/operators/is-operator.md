---
title: "Is Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.is"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparison operators"
  - "equivalent objects"
  - "TypeOf...Is expression"
  - "Is operator [Visual Basic]"
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Is Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Compare deux variables référence d'objet.  
  
## Syntaxe  
  
```  
  
result = object1 Is object2  
```  
  
## Composants  
 `result`  
 Obligatoire.  Toute valeur `Boolean`.  
  
 `object1`  
 Obligatoire.  Tout nom `Object`.  
  
 `object2`  
 Obligatoire.  Tout nom `Object`.  
  
## Notes  
 L'opérateur `Is` détermine si deux références d'objet font référence au même objet.  Toutefois, il n'effectue pas de comparaisons de valeurs.  Si `object1` et `object2` font référence à la même instance d'objet, `result` a la valeur `True` ; sinon, `result` a la valeur `False`.  
  
 `Is` peut être utilisé également avec le mot clé `TypeOf` pour créer une expression `TypeOf`...`Is` qui teste si une variable d'objet est compatible avec un type de données.  
  
> [!NOTE]
>  Le mot clé `Is` est aussi utilisé dans [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `Is` pour comparer des paires de références d'objet.  Les résultats sont assignés à une valeur `Boolean` indiquant si les deux objets sont identiques.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Comme indiqué dans l'exemple précédent, vous pouvez utiliser l'opérateur `Is` pour tester des objets à liaison anticipée et à liaison tardive.  
  
## Voir aussi  
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)