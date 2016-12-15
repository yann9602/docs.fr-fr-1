---
title: "How to: Determine Whether Two Objects Are Identical (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "testing, objects"
  - "objects [Visual Basic], comparing"
  - "object variables, determining identity"
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Determine Whether Two Objects Are Identical (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], deux références de variable sont considérées comme identiques si leurs pointeurs sont semblables, c'est\-à\-dire si les deux variables pointent vers la même instance de classe en mémoire.  Par exemple, dans une application Windows Forms, vous pouvez effectuer une comparaison afin de déterminer si l'instance actuelle `Me` est identique à une instance particulière, telle que `Form2`.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit deux opérateurs pour comparer des pointeurs.  [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) retourne la valeur `True` si les objets sont identiques et [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) retourne la valeur `True` dans le cas contraire.  
  
## Comment déterminer si deux objets sont identiques  
  
#### Pour déterminer si deux objets sont identiques  
  
1.  Configurez une expression `Boolean` pour tester les deux objets.  
  
2.  Dans votre expression de test, utilisez l'opérateur `Is` avec les deux objets comme opérandes.  
  
     `Is` retourne `True` si les objets pointent vers la même instance de classe.  
  
## Comment déterminer si deux objets ne sont pas identiques  
 Vous souhaitez parfois exécuter une action si les deux objets ne sont pas identiques, mais il peut être délicat de combiner `Not` et `Is`, par exemple `If Not obj1 Is obj2`.  Dans ce cas, vous pouvez utiliser l'opérateur `IsNot`.  
  
#### Pour déterminer si deux objets ne sont pas identiques  
  
1.  Configurez une expression `Boolean` pour tester les deux objets.  
  
2.  Dans votre expression de test, utilisez l'opérateur `IsNot` avec les deux objets comme opérandes.  
  
     `IsNot` retourne `True` si les objets ne pointent pas vers la même instance de classe.  
  
## Exemple  
 L'exemple suivant teste des paires de variables `Object` pour vérifier si elles pointent vers la même instance de classe.  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 L'exemple précédent affiche la sortie suivante.  
  
 `objA different from objB?  True`  
  
 `objA identical to objC?  True`  
  
## Voir aussi  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)