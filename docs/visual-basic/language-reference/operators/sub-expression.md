---
title: "Sub Expression (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic], sub expression"
  - "Sub Expression [Visual Basic]"
  - "subroutines [Visual Basic], sub expressions"
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Sub Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare les paramètres et le code qui définissent une expression lambda de sous\-routine.  
  
## Syntaxe  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`parameterlist`|Facultatif.  Liste des noms de variables locales représentant les paramètres de la procédure.  Les parenthèses doivent être présentes même quand la liste est vide.  Pour plus d'informations, consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Obligatoire.  Instruction unique.|  
|`statements`|Obligatoire.  Liste d'instructions.|  
  
## Notes  
 Une *expression lambda* est une sous\-routine qui n'a pas de nom et qui exécute une ou plusieurs instructions.  Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu'argument à `RemoveHandler`.  Pour plus d'informations sur les délégués et l'utilisation d'expressions lambda avec les délégués, consultez [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) et [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Syntaxe d'expression lambda  
 La syntaxe d'une expression lambda est similaire à celle d'une sous\-routine standard.  Les différences sont les suivantes :  
  
-   Une expression lambda n'a pas de nom.  
  
-   Une expression lambda ne peut pas avoir de modificateur, tel que `Overloads` ou `Overrides`.  
  
-   Le corps d'une expression lambda sur une ligne doit être une instruction, pas une expression.  Le corps peut se composer d'un appel à une sous\-procédure, mais pas d'un appel à une procédure de fonction.  
  
-   Dans une expression lambda, soit tous les paramètres doivent avoir des types de données spécifiés, soit tous les paramètres doivent être déduits.  
  
-   Les paramètres facultatifs et `ParamArray` ne sont pas autorisés dans les expressions lambda.  
  
-   Les paramètres génériques ne sont pas autorisés dans les expressions lambda.  
  
## Exemple  
 L'exemple suivant présente une expression lambda qui écrit une valeur sur la console.  L'exemple montre la syntaxe d'expression lambda sur une ou plusieurs lignes d'une sous\-routine.  Pour plus d'exemples, consultez [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## Voir aussi  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)