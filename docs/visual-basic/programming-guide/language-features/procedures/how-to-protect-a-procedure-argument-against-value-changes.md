---
title: "How to: Protect a Procedure Argument Against Value Changes (Visual Basic) | Microsoft Docs"
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
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "arguments [Visual Basic], passing by reference"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Protect a Procedure Argument Against Value Changes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Si une procédure déclare un paramètre comme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] donne au code de procédure une référence directe à l'élément de programmation sous\-jacent à l'argument dans le code appelant.  Cela permet à la procédure de modifier la valeur sous\-jacente à l'argument dans le code appelant.  Il peut arriver que le code appelant tente de se protéger contre une telle modification.  
  
 Vous pouvez toujours protéger un argument d'une modification en déclarant le paramètre [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) correspondant dans la procédure.  Si vous voulez avoir la possibilité de modifier un argument donné lorsque vous le souhaitez, vous pouvez le déclarer `ByRef` et laisser le code appelant déterminer le mécanisme de passage pour chaque appel.  Il procède en mettant l'argument correspondant entre parenthèses pour le passer par valeur, ou en ne le mettant pas entre parenthèses pour le passer par référence.  Pour plus d'informations, consultez [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md).  
  
## Exemple  
 L'exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments.  La procédure `increase` ajoute simplement la valeur 1 à chaque élément.  La procédure `replace` assigne un nouveau tableau au paramètre `a()`, puis ajoute la valeur 1 à chaque élément.  Cependant, la réassignation n'affecte pas la variable tableau sous\-jacente dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 Le premier appel `MsgBox` affiche "After increase\(n\): 11, 21, 31, 41".  Étant donné que le tableau  `n`  est un type référence,  `replace`  peut modifier ses membres, même si le mécanisme de passage est `ByVal`.  
  
 Le second appel `MsgBox` affiche "After replace\(n\): 11, 21, 31, 41".  Étant donné que  `n`  est passé `ByVal`,  `replace`  ne peut pas modifier la variable  `n`  dans le code appelant en lui assignant un nouveau tableau.  Lorsque  `replace`  crée la nouvelle instance de tableau  `k`  et l'assigne à la variable locale  `a`, il perd la référence à  `n`  passée par le code appelant.  Lorsqu'il modifie les membres de  `a`, seul le tableau local  `k`  est affecté.  Par conséquent,  `replace`  n'incrémente pas les valeurs du tableau  `n`  dans le code appelant.  
  
## Compilation du code  
 Le comportement par défaut en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer les arguments par valeur.  En programmation, il est toutefois conseillé d'ajouter le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) avec chaque argument déclaré.  Cela rend votre code plus lisible.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)