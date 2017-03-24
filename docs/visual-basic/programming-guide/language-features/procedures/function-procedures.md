---
title: "Fonction procédures (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 11baaa6985f0681aa9c67c4f2470fb9917db5b78
ms.lasthandoff: 03/13/2017

---
# <a name="function-procedures-visual-basic"></a>Procédures Function (Visual Basic)
A `Function` procédure est une série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instructions placées par le `Function` et `End Function` instructions. Le `Function` procédure effectue une tâche, puis retourne le contrôle au code appelant. Lorsqu’elle retourne le contrôle, elle retourne également une valeur au code appelant.  
  
 Chaque fois que la procédure est appelée, ses instructions sont exécutées, commençant par la première instruction exécutable après le `Function` instruction et se terminant par la première `End Function`, `Exit Function`, ou `Return` instruction rencontrée.  
  
 Vous pouvez définir un `Function` procédure dans un module, classe ou structure. Il est `Public` par défaut, ce qui signifie que vous pouvez l’appeler depuis n’importe où dans votre application qui a accès au module, classe ou une structure dans laquelle vous définie.  
  
 Un `Function` procédure peut prendre des arguments, tels que les constantes, variables ou expressions qui sont passées par le code appelant.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’un `Function` comme suit :  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 Le *modificateurs* peut spécifier des informations concernant la surcharge, substitution, le partage et l’occultation et niveau d’accès. Pour plus d’informations, consultez [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Vous déclarez chaque paramètre de la même façon que pour [procédures Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Type de données  
 Chaque `Function` procédure possède un type de données, fait de simplement chaque variable. Ce type de données est spécifié par le `As` clause dans la `Function` instruction, qui détermine le type de données de la valeur de la fonction retourne au code appelant. Les exemples de déclarations suivants illustrent ce principe.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Pour plus d’informations, consultez « Parties » dans [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Retour de valeurs  
 La valeur un `Function` procédure envoie la restauration vers le code appelant est appelée sa valeur de retour. La procédure retourne cette valeur de deux manières :  
  
-   Il utilise le `Return` pour spécifier la valeur de retour et retourne le contrôle immédiatement au programme appelant. L'exemple suivant illustre ce comportement.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Il assigne une valeur à son propre nom de fonction dans une ou plusieurs instructions de la procédure. Contrôle ne retourne pas au programme appelant jusqu'à un `Exit Function` ou `End Function` instruction est exécutée. L'exemple suivant illustre ce comportement.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 L’avantage de l’affectation de la valeur de retour pour le nom de fonction est que le contrôle ne retourne pas de la procédure, jusqu'à ce qu’il rencontre un `Exit Function` ou `End Function` instruction. Cela permet d’assigner une valeur préliminaire et l’ajuster ultérieurement si nécessaire.  
  
 Pour plus d’informations sur les valeurs de retour, voir [Function, instruction](../../../../visual-basic/language-reference/statements/function-statement.md). Pour plus d’informations sur le renvoi des tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez un `Function` procédure en incluant son nom et ses arguments soit à droite d’une instruction d’assignation ou dans une expression. Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez omettre les parenthèses.  
  
 La syntaxe d’un appel à une `Function` comme suit :  
  
 *lvalue*`=`*functionname* `[(` *argumentlist*    `)]`  
  
 `If ((`*functionname* `[(` *argumentlist* `)] / 3) <=` *expression*  `) Then`  
  
 Lorsque vous appelez un `Function` procédure, il est inutile d’utiliser sa valeur de retour. Si vous ne le faites pas, toutes les actions de la fonction sont exécutées, mais la valeur de retour est ignorée. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>est souvent appelée de cette manière.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 Les éléments suivants `Function` procédure calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, d’après les valeurs des deux autres côtés.  
  
 [!code-vb[VbVbcnProcedures n °&1;](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 L’exemple suivant montre un appel typique à `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures n °&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Function (instruction)](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Comment : retourner une valeur d’une procédure](./how-to-return-a-value-from-a-procedure.md)   
 [Guide pratique : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)
