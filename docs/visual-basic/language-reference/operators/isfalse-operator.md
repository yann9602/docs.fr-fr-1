---
title: "IsFalse Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.isfalse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AndAlso operator"
  - "IsFalse operator"
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsFalse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Détermine si une expression est `False`.  
  
 Vous ne pouvez pas appeler explicitement `IsFalse` dans votre code, mais le compilateur Visual Basic peut l'utiliser pour générer le code à partir de clauses `AndAlso`.  Si vous définissez une classe ou structure, puis utilisez une variable de ce type dans une clause `AndAlso`, vous devez définir `IsFalse` sur cette classe ou structure.  
  
 Le compilateur considère les opérateurs `IsFalse` et `IsTrue` comme une *paire équilibrée*.  Cela signifie que si vous définissez l'un, vous devez également définir l'autre.  
  
> [!NOTE]
>  L'opérateur `IsFalse` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple de code suivant définit le plan d'une structure qui inclut des définitions pour les opérateurs `IsFalse` et `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## Voir aussi  
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)