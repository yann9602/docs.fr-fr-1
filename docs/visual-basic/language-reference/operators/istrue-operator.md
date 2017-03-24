---
title: "IsTrue Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.istrue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsTrue operator"
  - "OrElse operator [Visual Basic]"
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# IsTrue Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Détermine si une expression est `True`.  
  
 Vous ne pouvez pas appeler explicitement `IsTrue` dans votre code, mais le compilateur Visual Basic peut l'utiliser pour générer le code à partir de clauses `OrElse`.  Si vous définissez une classe ou structure, puis utilisez une variable de ce type dans une clause `OrElse`, vous devez définir `IsTrue` sur cette classe ou structure.  
  
 Le compilateur considère les opérateurs `IsTrue` et `IsFalse` comme une *paire équilibrée*.  Cela signifie que si vous définissez l'un, vous devez également définir l'autre.  
  
## Utilisation de IsTrue par le compilateur  
 Lorsque vous avez défini une classe ou structure, vous pouvez utiliser une variable de ce type dans une instruction `For`, `If`, `Else` `If` ou `While`, ou dans une clause `When`.  Si vous faites ceci, le compilateur requiert un opérateur qui convertit votre type en une valeur `Boolean` de façon à pouvoir tester une condition.  Il recherche un opérateur adéquat dans l'ordre suivant :  
  
1.  Un opérateur de conversion étendue de votre classe ou structure en `Boolean`.  
  
2.  Un opérateur de conversion étendue de votre classe ou structure en `Boolean?`.  
  
3.  L'opérateur `IsTrue` de votre classe ou structure.  
  
4.  Conversion restrictive vers `Boolean?` qui n'implique pas de conversion de `Boolean` à `Boolean?`.  
  
5.  Un opérateur de conversion restrictive de votre classe ou structure en `Boolean`.  
  
 Si vous n'avez pas défini de conversion en `Boolean` ou d'opérateur `IsTrue`, le compilateur signale une erreur.  
  
> [!NOTE]
>  L'opérateur `IsTrue` peut être *surchargé*, ce qui signifie qu'une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure.  Si votre code utilise cet opérateur sur une telle classe ou structure, assurez\-vous que vous comprenez son comportement redéfini.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemple  
 L'exemple de code suivant définit le plan d'une structure qui inclut des définitions pour les opérateurs `IsFalse` et `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## Voir aussi  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)