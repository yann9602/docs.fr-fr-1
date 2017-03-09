---
title: "While...End While Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.While"
  - "vb.While...EndWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "While statement, While...End While"
  - "While statement"
  - "While...End While statements"
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# While...End While Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Exécute une série d'instructions tant qu'une condition donnée a la valeur `True`.  
  
## Syntaxe  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`condition`|Requis.  Expression `Boolean`.  Si `condition` est `Nothing`, Visual Basic le traite comme `False`.|  
|`statements`|Optionnel.  Une ou plusieurs instructions suivant `While` et s'exécutant chaque fois que `condition` a la valeur `True`.|  
|`Continue While`|Optionnel.  Transfère le contrôle à l'itération suivante du bloc d' `While` .|  
|`Exit While`|Optionnel.  Transfert le contrôle hors du bloc `While`.|  
|`End While`|Requis.  Met fin à la définition du bloc `While`.|  
  
## Notes  
 Utilisez une structure `While...End While` lorsque vous souhaitez répéter indéfiniment un ensemble d'instructions, tant qu'une condition reste `True`.  Si vous souhaitez plus de souplesse à l'égard de l'emplacement où vous testez la condition ou du résultat pour lequel vous la testez, vous préférez certainement [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).  Si vous souhaitez répéter plusieurs fois les instructions, [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md) constitue généralement un meilleur choix.  
  
> [!NOTE]
>  Le mot clé `While` est aussi utilisé dans [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) et [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Si `condition` est `True`, toutes les `statements` s'exécutent jusqu'à ce que l'instruction `End While` soit rencontrée.  Le contrôle retourne ensuite à l'instruction d' `While` , et `condition` est encore contrôlé.  Si `condition` est toujours `True`, le processus est répété.  Si c'est `False`, le contrôle passe à l'instruction qui suit l'instruction d' `End While` .  
  
 L'instruction d' `While` contrôle toujours la condition avant qu'elle démarre la boucle.  La boucle continue tant que la condition est `True`.  Si `condition` est `False` lorsque vous écrivez d'abord la boucle, elle ne fonctionne pas même une fois.  
  
 `condition` résulte généralement d'une comparaison de deux valeurs, mais elle peut être une expression qui correspond à [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) une valeur \(`True` ou `False`\).  Cette expression peut inclure une valeur d'un autre type de données, tel qu'un type numérique, qui a été converti en `Boolean`.  
  
 Vous pouvez imbriquer les boucles `While` en plaçant une boucle à l'intérieur d'une autre.  Vous pouvez également imbriquer divers types de structures de contrôle l'un dans l'autre.  Pour plus d'informations, consultez [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Quittez while  
 L'instruction de [Quittez while](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre manière de quitter une boucle d' `While` .  d'`Exit While` transfère le contrôle immédiatement à l'instruction qui suit l'instruction d' `End While` .  
  
 Vous utilisez généralement `Exit While` après qu'une condition soit évaluée \(par exemple, dans une structure d' `If...Then...Else` \).  Vous pouvez éventuellement quitter une boucle si vous décelez une condition qui la rend inutile ou impossible pour poursuivre l'itération, telle qu'une valeur erronée ou une demande d'arrêt.  Vous pouvez utiliser `Exit While` lorsque vous définissez une condition qui peut provoquer *une boucle sans fin*, qui est une boucle qui peut exécuter un nombre de fois extrêmement volumineux ou même infini.  Vous pouvez ensuite utiliser `Exit While` pour échapper la boucle.  
  
 Vous pouvez placer un nombre quelconque d'instructions `Exit While` n'importe où dans la boucle `While`.  
  
 Utilisée dans des boucles `While` imbriquées, l'instruction `Exit While` transfère le contrôle en dehors de la boucle la plus profonde et au niveau d'imbrication supérieur suivant.  
  
 D' `Continue While` d'instruction transfère le contrôle immédiatement à l'itération suivante de la boucle.  Pour plus d'informations, consultez [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## Exemple  
 Dans l'exemple suivant, les instructions dans la boucle poursuivent leur exécution jusqu'à ce que la variable `index` soit supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/while-end-while-statement_1.vb)]  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation des instructions `Continue While` et `Exit While`.  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/while-end-while-statement_2.vb)]  
  
## Exemple  
 L'exemple suivant lit toutes les lignes dans un fichier texte.  La méthode <xref:System.IO.File.OpenText%2A> ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères.  Dans l'état d' `While` , la méthode d' <xref:System.IO.StreamReader.Peek%2A> d' `StreamReader` détermine si le fichier contient des caractères spéciaux.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/while-end-while-statement_3.vb)]  
  
## Voir aussi  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)