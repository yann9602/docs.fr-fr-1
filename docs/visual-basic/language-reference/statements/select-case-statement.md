---
title: "Select...Case Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Select"
  - "vb.Case"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Case statement"
  - "Select...Case statements"
  - "conditional statements, Select Case"
  - "control flow, branching"
  - "Else keyword [Visual Basic], in Select...Case statements"
  - "execution, conditional"
  - "To keyword, in Select...Case statements"
  - "Select Case statement, Select...Case"
  - "Select statement, Select...Case"
  - "Is operator [Visual Basic], in Select...Case statements"
  - "branching, conditional"
  - "Case Else statement, Select...Case"
  - "End keyword, Select Case statements"
  - "Case statement, Select...Case"
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Select...Case Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Exécute un groupe d'instructions parmi plusieurs autres, selon la valeur d'une expression.  
  
## Syntaxe  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`testexpression`|Obligatoire.  Expression.  Doit avoir pour valeur l'un des types de données élémentaires \(`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong` et `UShort`\).|  
|`expressionlist`|Obligatoire dans une instruction `Case`.  Liste des clauses d'expression représentant les valeurs correspondantes pour `testexpression`.  Plusieurs clauses d'expression sont séparées par des virgules.  Chaque clause peut prendre l'une des formes suivantes :<br /><br /> -   *expression1* `To` *expression2*<br />-   \[ `Is` \] *OpérateurComparaison* *expression*<br />-   *expression*<br /><br /> Le mot clé `To` permet de définir les limites d'une plage de valeurs correspondantes pour `testexpression`.  La valeur de `expression1` doit être inférieure ou égale à la valeur de `expression2`.<br /><br /> Utilisez le mot clé `Is` avec un opérateur de comparaison \(`=`, `<>`, `<`, `<=`, `>` ou `>=`\) pour spécifier une restriction sur les valeurs correspondantes pour `testexpression`.  Si le mot clé `Is` n'est pas indiqué, il est automatiquement inséré avant l'*OpérateurComparaison*.<br /><br /> La syntaxe indiquant uniquement `expression` est traitée comme un cas spécial de la syntaxe `Is` où *OpérateurComparaison* représente le signe égal \(`=`\).  Cette syntaxe est évaluée en tant que `testexpression` \= `expression`.<br /><br /> Les expressions de `expressionlist` peuvent correspondre à n'importe quel type de données, si elles peuvent être implicitement converties au type de `testexpression` et si l'argument `comparisonoperator` correspondant est valide pour les deux types avec lesquels il est utilisé.|  
|`statements`|Facultatif.  Une ou plusieurs instructions qui suivent `Case` s'exécutent si `testexpression` correspond à une clause dans `expressionlist`.|  
|`elsestatements`|Facultatif.  Une ou plusieurs instructions qui suivent `Case Else` s'exécutent si `testexpression` ne correspond pas à une clause dans `expressionlist` de l'une des instructions `Case`.|  
|`End Select`|Met fin à la définition de la construction `Select`...`Case`.|  
  
## Notes  
 Si `testexpression` correspond à une clause `Case` `expressionlist`, les instructions qui suivent cette instruction `Case` s'exécutent dans la prochaine instruction `Case`, `Case Else` ou `End Select`.  L'instruction qui suit `End Select` prend ensuite le contrôle.  Si `testexpression` correspond à une clause `expressionlist` dans plusieurs clauses `Case`, seules les instructions qui suivent la première correspondance s'exécutent.  
  
 L'instruction `Case Else` permet d'indiquer que `elsestatements` doit être exécuté si aucune correspondance n'existe entre `testexpression` et une clause `expressionlist` dans l'une des autres instructions `Case`.  Bien que cela ne soit pas indispensable, la présence d'une instruction `Case Else` dans votre construction `Select Case` peut être utile lorsque `testexpression` prend des valeurs inattendues.  Si aucune clause `Case` `expressionlist` ne correspond à `testexpression` et si aucune instruction `Case Else` n'existe, le contrôle passe à l'instruction après `End Select`.  
  
 Vous pouvez utiliser plusieurs expressions ou plages dans chaque clause `Case`.  Par exemple, la ligne suivante est valide.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  Le mot clé `Is` utilisé dans les instructions `Case` et `Case Else` est identique à [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), qui est utilisé pour la comparaison de référence d'objet.  
  
 Vous pouvez indiquer des plages et des expressions multiples pour des chaînes de caractères.  Dans l'exemple suivant, `Case` correspond à une chaîne qui est exactement égale à "apples", qui a une valeur entre "nuts" et "soup" dans l'ordre alphabétique ou qui contient la même valeur exacte que la valeur actuelle de `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 La définition de `Option Compare` peut affecter les comparaisons de chaînes.  Sous `Option Compare Text`, les chaînes "Apples" et "apples" sont considérées comme égales, mais pas sous `Option Compare Binary`.  
  
> [!NOTE]
>  Une instruction `Case` contenant plusieurs clauses peut exposer un comportement appelé *court\-circuit*.  Visual Basic évalue les clauses de la gauche vers la droite, et si une correspondance existe avec `testexpression`, les autres clauses ne sont pas évaluées.  Le court\-circuit peut améliorer les performances, mais il peut engendrer des résultats inattendus si chaque expression dans `expressionlist` doit être évaluée.  Pour plus d'informations sur le court\-circuit, consultez [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Si le code contenu dans un bloc d'instruction `Case` ou `Case Else` ne doit pas exécuter d'autres instructions du bloc, il peut quitter le bloc en utilisant l'instruction `Exit Select`.  L'instruction qui suit `End Select` prend alors immédiatement le contrôle.  
  
 Les constructions `Select Case` peuvent être imbriquées.  Chaque construction `Select Case` imbriquée doit avoir une instruction `End Select` correspondante et doit être entièrement contenue dans un bloc d'instruction `Case` ou `Case Else` unique de la construction `Select Case` externe dans laquelle elle est imbriquée.  
  
## Exemple  
 L'exemple ci\-dessous utilise une construction `Select Case` pour écrire une ligne correspondant à la valeur de la variable `number`.  La seconde instruction `Case` contient la valeur qui correspond à la valeur actuelle de `number`. Ainsi, l'instruction qui écrit « Entre 6 et 8 inclus » est exécutée.  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)