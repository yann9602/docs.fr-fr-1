---
title: "If Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.IfOperator"
  - "IfOperator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ternary operators"
  - "conditional execution"
  - "If expressions [Visual Basic]"
  - "conditional operator [Visual Basic]"
  - "If Operator [Visual Basic]"
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# If Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilise l'évaluation de court\-circuit pour retourner conditionnellement l'une de deux valeurs.  L'opérateur `If` peut être appelé avec trois arguments ou avec deux arguments.  
  
## Syntaxe  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## Opérateur If appelé avec trois arguments  
 Lorsque l'opérateur `If` est appelé à l'aide de trois arguments, le premier argument doit être évalué à une valeur pouvant être castée en tant que `Boolean`.  Cette valeur `Boolean` détermine lequel des deux autres arguments est évalué et retourné.  La liste qui suit s'applique uniquement lorsque l'opérateur `If` est appelé en utilisant trois arguments.  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`argument1`|Obligatoire.  `Boolean`.  Détermine lequel des autres arguments doit être évalué et retourné.|  
|`argument2`|Obligatoire.  `Object`.  Évalué et retourné si `argument1` est évalué à `True`.|  
|`argument3`|Obligatoire.  `Object`.  Évaluée et retournée si `argument1` correspond à `False` ou si `argument1` est une variable de [nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` qui correspond à [rien](../../../visual-basic/language-reference/nothing.md).|  
  
 Un opérateur `If` appelé avec trois travaux d'arguments agit comme une fonction `IIf`, à cette exception près qu'il utilise l'évaluation de court\-circuit.  Une fonction `IIf` évalue toujours les trois arguments, alors qu'un opérateur `If` qui a trois arguments n'en évalue que deux.  Le premier argument `If` est évalué et le résultat est casté en tant que valeur `Boolean`, `True` ou `False`.  Si la valeur est `True`, `argument2` est évalué et sa valeur est retournée, mais `argument3` n'est pas évalué.  Si la valeur de l'expression `Boolean` est `False`, `argument3` est évalué et sa valeur est retournée, mais `argument2` n'est pas évalué.  Les exemples suivants illustrent l'utilisation de l'opérateur `If` lorsque trois arguments sont utilisés :  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 L'exemple suivant illustre la valeur d'évaluation de court\-circuit.  L'exemple affiche deux tentatives de diviser la variable `number` par la variable `divisor`, sauf lorsque le `divisor` est nul.  Dans ce cas, une valeur 0 doit être retournée, et aucune tentative ne doit être faite pour effectuer la division, puisqu'une erreur d'exécution en résulterait.  L'expression `If` utilisant l'évaluation de court\-circuit, elle évalue soit le deuxième soit le troisième argument, en fonction de la valeur du premier argument.  Si le premier argument est vrai, le diviseur n'est pas nul : l'évaluation du deuxième argument et la division peuvent se faire en toute sécurité.  Si le premier argument est faux, seul le troisième argument est évalué et un 0 est retourné.  Par conséquent, lorsque le diviseur est 0, aucune tentative n'est faite pour effectuer la division et aucune erreur n'en résulte.  Toutefois, l'expression `IIf` n'utilisant pas l'évaluation de court\-circuit, le deuxième argument est évalué même lorsque le premier argument est faux.  Le résultat est une erreur de division par zéro à l'exécution.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## Opérateur If appelé avec deux arguments  
 Le premier argument à `If` peut être omis.  Cela permet à l'opérateur d'être appelé en n'utilisant que deux arguments.  La liste qui suit s'applique uniquement lorsque l'opérateur `If` est appelé avec deux arguments.  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`argument2`|Obligatoire.  `Object`.  Doit être un type référence ou Nullable.  Évalué et retourné lorsqu'il s'évalue à une valeur quelle qu'elle soit, différente de `Nothing`.|  
|`argument3`|Obligatoire.  `Object`.  Évalué et retourné si `argument2` est évalué à `Nothing`.|  
  
 Lorsque l'argument `Boolean` est omis, le premier argument doit être une référence ou un type Nullable.  Si le premier argument s'évalue à la valeur `Nothing`, la valeur du deuxième argument est retournée.  Dans tous les autres cas, la valeur du premier argument est retournée.  L'exemple suivant illustre comment cette évaluation fonctionne.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)