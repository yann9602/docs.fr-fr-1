---
title: "IsNot Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.isnot"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsNot operator"
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsNot Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Compare deux variables référence d'objet.  
  
## Syntaxe  
  
```  
  
result = object1 IsNot object2  
```  
  
## Composants  
 `result`  
 Obligatoire.  Valeur `Boolean`.  
  
 `object1`  
 Obligatoire.  Toute variable ou expression `Object`.  
  
 `object2`  
 Obligatoire.  Toute variable ou expression `Object`.  
  
## Notes  
 L'opérateur `IsNot` détermine si deux références d'objet font référence des objets différents.  Toutefois, il n'effectue pas de comparaisons de valeurs.  Si `object1` et `object2` font référence à la même instance d'objet, `result` a la valeur `False` ; sinon, `result` a la valeur `True`.  
  
 `IsNot` est le contraire de l'opérateur `Is`.  `IsNot` a l'avantage de vous faire éviter la syntaxe difficile avec `Not` et `Is`, qui peuvent être difficiles à lire.  
  
 Vous pouvez utiliser les opérateurs `Is` et `IsNot` pour tester des objets à liaison anticipée et à liaison tardive.  
  
> [!NOTE]
>  L'opérateur `IsNot` ne peut pas être utilisé pour comparer des expressions retournées par l'opérateur `TypeOf`.  À la place, vous devez utiliser les opérateurs `Is` et `Not`.  
  
## Exemple  
 L'exemple de code suivant utilise à la fois l'opérateur `Is` et l'opérateur `IsNot` pour effectuer la même comparaison.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## Voir aussi  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [How to: Test Whether Two Objects Are the Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)