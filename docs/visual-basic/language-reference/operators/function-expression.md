---
title: "Function Expression (Visual Basic) | Microsoft Docs"
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
  - "Function expression [Visual Basic]"
  - "functions [Visual Basic], function expressions"
  - "lambda expressions [Visual Basic], function expression"
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare les paramètres et le code qui définissent une expression lambda de fonction.  
  
## Syntaxe  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`parameterlist`|Facultatif.  Liste des noms de variables locales représentant les paramètres de cette procédure.  Les parenthèses doivent être présentes même quand la liste est vide.  Consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Obligatoire.  Une expression unique.  Le type de l'expression est le type de retour de la fonction.|  
|`statements`|Obligatoire.  Liste d'instructions qui retourne une valeur à l'aide de l'instruction `Return`.  \(Consultez [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).\) Le type de la valeur retournée est le type de retour de la fonction.|  
  
## Notes  
 Une *expression lambda* est une fonction sans nom qui calcule et retourne une valeur.  Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu'argument à `RemoveHandler`.  Pour plus d'informations sur les délégués et l'utilisation d'expressions lambda avec les délégués, consultez [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) et [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Syntaxe d'expression lambda  
 La syntaxe d'une expression lambda ressemble à celle d'une fonction standard.  Les différences sont les suivantes :  
  
-   Une expression lambda n'a pas de nom.  
  
-   Les expressions lambda ne peuvent pas avoir modificateurs, tels que `Overloads` ou `Overrides`.  
  
-   Les expressions lambda n'utilisent pas de clause `As` pour désigner le type de retour de la fonction.  Au lieu de cela, le type est déduit de la valeur du corps d'une expression lambda à une seule ligne, ou de la valeur de retour d'une expression lambda multiligne.  Par exemple, si le corps d'une expression lambda sur une ligne est `Where cust.City = "London"`, son type de retour est `Boolean`.  
  
-   Le corps d'une expression lambda sur une ligne doit être une expression, pas une instruction.  Le corps peut se composer d'un appel à une procédure de fonction, mais pas d'un appel à une sous\-procédure.  
  
-   Tous les paramètres doivent posséder des types de données spécifiés ou être tous déduits.  
  
-   Les paramètres facultatifs et Paramarray ne sont pas autorisés.  
  
-   Les paramètres génériques ne sont pas autorisés.  
  
## Exemple  
 Les exemples suivants illustrent deux façons de créer des expressions lambda simples.  La première utilise un `Dim` pour fournir un nom pour la fonction.  Pour appeler la fonction, envoyez une valeur pour le paramètre.  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## Exemple  
 Vous pouvez également déclarer et exécuter simultanément la fonction.  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## Exemple  
 L'exemple suivant est une expression lambda qui incrémente son argument et retourne la valeur.  L'exemple montre la syntaxe d'expression lambda sur une ou plusieurs lignes d'une fonction.  Pour plus d'exemples, consultez [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## Exemple  
 Les expressions lambda sont à la base d'un grand nombre d'opérateurs de requête dans [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]et peuvent être utilisées explicitement dans les requêtes basées sur une méthode.  L'exemple suivant montre une requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] typique, suivie de la traduction de la requête au format de la méthode.  
  
```vb#  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Pour plus d'informations sur les méthodes de requête, consultez [Queries](../../../visual-basic/language-reference/queries/queries.md).  Pour plus d'informations sur les opérateurs de requête standard, consultez [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## Voir aussi  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)