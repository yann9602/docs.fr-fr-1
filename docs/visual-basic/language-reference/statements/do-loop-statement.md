---
title: "Do...Loop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Do"
  - "vb.Loop"
  - "vb.Until"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional statements, Do…Loop"
  - "while statement, Do...Loop"
  - "execution, conditional"
  - "Do loops"
  - "Until keyword, Do...Loop statement"
  - "Do...Loop statement"
  - "instructions, repeating"
  - "Do statement"
  - "Exit statement, in Do...Loop statements"
  - "loop structures, Do…Loop statements"
  - "do-while statements"
  - "loops, exiting"
  - "Loop keyword, Do...Loop statement"
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Do...Loop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Répète un bloc d'instructions tant qu'une condition `Boolean` a la valeur `True` ou jusqu'à ce que la condition devienne `True`.  
  
## Syntaxe  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`Do`|Requis.  Démarre la définition de la boucle `Do`.|  
|`While`|Obligatoire sauf si `Until` est utilisé.  Répétez la boucle jusqu'à ce que `condition` ait la valeur `False`.|  
|`Until`|Obligatoire sauf si `While` est utilisé.  Répétez la boucle jusqu'à ce que `condition` ait la valeur `True`.|  
|`condition`|Optionnel.  Expression `Boolean`.  Si `condition` est `Nothing`, Visual Basic le traite comme `False`.|  
|`statements`|Optionnel.  Une ou plusieurs instructions répétées tant que `condition` a la valeur `True`, ou jusqu'à ce qu'elle le devienne.|  
|`Continue Do`|Optionnel.  Transfère le contrôle à l'itération suivante de la boucle d' `Do` .|  
|`Exit Do`|Optionnel.  Transfère le contrôle en dehors de la boucle `Do`.|  
|`Loop`|Requis.  Met fin à la définition de la boucle `Do`.|  
  
## Notes  
 Utilisez une structure `Do...Loop` lorsque vous souhaitez répéter un ensemble d'instructions un nombre indéfini de fois, jusqu'à ce qu'une condition soit satisfaite.  Si vous souhaitez répéter les instructions un nombre défini de fois, il est préférable d'utiliser [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Vous pouvez utiliser `While` ou `Until` pour spécifier `condition`, mais pas les deux.  
  
 Vous ne pouvez tester `condition` qu'une seule fois, au début ou à la fin de la boucle.  Si vous testez la `condition` au début de la boucle \(dans l'instruction `Do`\), la boucle peut ne jamais s'exécuter, même une fois.  Si vous la testez à la fin de la boucle \(dans l'instruction `Loop`\), la boucle s'exécute toujours, au moins une fois.  
  
 La condition provient généralement d'une comparaison entre deux valeurs, mais elle peut être une expression qui évalue une valeur [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) \(`True` ou `False`\).  Elle peut comprendre des valeurs d'autres types de données, tels que des types numériques, qui ont été converties en type `Boolean`.  
  
 Vous pouvez imbriquer les boucles `Do` en plaçant une boucle à l'intérieur d'une autre.  Vous pouvez également imbriquer divers types de structures de contrôle l'un dans l'autre.  Pour plus d'informations, consultez [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  La structure `Do...Loop` offre plus de flexibilité que [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) car elle vous permet de mettre fin à la boucle lorsque `condition` n'a plus la valeur `True` ou lorsqu'elle prend la valeur `True`.  Cela vous permet également de tester `condition` au début ou la fin de la boucle.  
  
## Exit Do  
 L'instruction [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une solution alternative pour sortir d'une `Do…Loop`.  L'instruction du type `Exit Do` passe immédiatement le contrôle à l'instruction qui suit l'instruction `Loop`.  
  
 `Exit Do` est souvent utilisé après avoir évalué la condition, par exemple dans une structure `If...Then...Else`.  Vous pouvez éventuellement quitter une boucle si vous décelez une condition qui la rend inutile ou impossible pour poursuivre l'itération, telle qu'une valeur erronée ou une demande d'arrêt.  Vous pouvez utiliser `Exit Do` pour tester une condition qui engendrerait une *boucle infinie*, c'est\-à\-dire une boucle qui pourrait s'exécuter de nombreuses fois, voire indéfiniment.  Vous pouvez utiliser `Exit Do` pour abandonner la boucle.  
  
 Vous pouvez inclure n'importe quel nombre d'instructions `Exit Do`, n'importe où dans une `Do…Loop`.  
  
 Utilisée dans des boucles `Do` imbriquées, l'instruction `Exit Do` transfère le contrôle en dehors de la boucle la plus profonde et au niveau d'imbrication supérieur suivant.  
  
## Exemple  
 Dans l'exemple suivant, les instructions dans la boucle poursuivent leur exécution jusqu'à ce que la variable `index` soit supérieure à 10.  La clause `Until` est à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant utilise une clause `While` au lieu d'une clause `Until`, et `condition` est testée au début plutôt qu'à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## Exemple  
 Dans l'exemple suivant, `condition` arrête la boucle lorsque la variable `index` est supérieure à 100.  Cependant, avec l'instruction `If` dans la boucle, l'instruction `Exit Do` arrête la boucle lorsque la variable d'index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## Exemple  
 L'exemple suivant lit toutes les lignes dans un fichier texte.  La méthode <xref:System.IO.File.OpenText%2A> ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.  Dans la condition `Do...Loop`, la méthode <xref:System.IO.StreamReader.Peek%2A> de `StreamReader` détermine s'il existe des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## Voir aussi  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)