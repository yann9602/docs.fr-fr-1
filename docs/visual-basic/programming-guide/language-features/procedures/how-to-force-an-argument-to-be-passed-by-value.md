---
title: "How to: Force an Argument to Be Passed by Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], in parentheses"
  - "procedure arguments, in parentheses"
  - "arguments [Visual Basic], changing value"
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Force an Argument to Be Passed by Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La déclaration de procédure détermine le mécanisme de passage.  Si un paramètre est déclaré [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit passer l'argument correspondant par référence.  Cela permet à la procédure de modifier la valeur de l'élément de programmation sous\-jacent à l'argument dans le code appelant.  Si vous souhaitez protéger l'élément sous\-jacent contre une telle modification, vous pouvez substituer le mécanisme de passage `ByRef` dans l'appel de procédure en plaçant le nom de l'argument entre parenthèses.  Ces parenthèses s'ajoutent aux parenthèses qui encadrent la liste d'arguments dans l'appel.  
  
 Le code appelant ne peut pas substituer un mécanisme [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
### Pour forcer le passage d'un argument par valeur  
  
-   Si le paramètre correspondant est déclaré comme `ByVal` dans la procédure, aucune étape supplémentaire n'est requise.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit déjà passer l'argument par valeur.  
  
-   Si le paramètre correspondant est déclaré `ByRef` dans la procédure, placez l'argument entre parenthèses dans l'appel de procédure.  
  
## Exemple  
 L'exemple suivant substitue une déclaration de paramètre `ByRef`.  Dans l'appel qui force `ByVal`, notez les deux niveaux de parenthèses.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Lorsque `str` est placé entre des parenthèses supplémentaires dans la liste d'arguments, la procédure `setNewString` ne peut pas modifier sa valeur dans le code appelant, et `MsgBox` affiche "Cannot be replaced if passed ByVal".  Lorsque `str` n'est pas placé entre des parenthèses supplémentaires, la procédure peut le modifier, et `MsgBox` affiche "This is a new value for the inString argument".  
  
## Compilation du code  
 Lorsque vous passez une variable par référence, vous devez utiliser le mot clé `ByRef` pour spécifier ce mécanisme.  
  
 Le comportement par défaut en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] consiste à passer les arguments par valeur.  En programmation, il est toutefois conseillé d'ajouter le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) avec chaque argument déclaré.  Cela rend votre code plus lisible.  
  
## Programmation fiable  
 Si une procédure déclare un paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), l'exécution correcte du code peut dépendre de la capacité à modifier l'élément sous\-jacent dans le code appelant.  Si le code appelant substitue ce mécanisme appelant en plaçant l'argument entre parenthèses ou s'il passe un argument non modifiable, la procédure ne peut pas modifier l'élément sous\-jacent.  Cela peut produire des résultats inattendus dans le code appelant.  
  
## Sécurité .NET Framework  
 Permettre à une procédure de modifier la valeur sous\-jacente à un argument dans le code appelant est toujours risqué.  Vérifiez que cette valeur doit bien être modifiée et préparez\-vous à en vérifier la validité avant de l'utiliser.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)