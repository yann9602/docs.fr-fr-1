---
title: "How to: Change the Value of a Procedure Argument (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], passing by reference"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Change the Value of a Procedure Argument (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous appelez une procédure, chaque argument que vous fournissez correspond à l'un des paramètres définis dans la procédure.  Dans certains cas, le code de procédure peut modifier la valeur sous\-jacente à un argument dans le code appelant.  Dans d'autres cas, la procédure peut modifier uniquement sa copie locale d'un argument.  
  
 Lorsque vous appelez la procédure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fait une copie locale de chaque argument auquel est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  Pour chaque argument auquel est passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] donne au code de procédure une référence directe à l'élément de programmation sous\-jacent à l'argument dans le code appelant.  
  
 Si l'élément sous\-jacent dans le code appelant est un élément modifiable et si `ByRef` est passé à l'argument, le code de procédure peut utiliser la référence directe pour modifier la valeur de l'élément dans le code appelant.  
  
## Modification de la valeur sous\-jacente  
  
#### Pour modifier la valeur sous\-jacente d'un argument de procédure dans le code appelant  
  
1.  Dans la déclaration de procédure, spécifiez [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour le paramètre correspondant à l'argument.  
  
2.  Dans le code appelant, passez un élément de programmation modifiable comme argument.  
  
3.  Dans le code appelant, ne mettez pas l'argument entre parenthèses dans la liste d'arguments.  
  
4.  Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à l'élément sous\-jacent dans le code appelant.  
  
 Consultez l'exemple ci\-dessous pour une démonstration.  
  
## Modification de copies locales  
 Si l'élément sous\-jacent dans le code appelant est un élément non modifiable ou si `ByVal` est passé à l'argument, la procédure ne peut pas modifier sa valeur dans le code appelant.  Toutefois, la procédure peut modifier sa copie locale d'un tel argument.  
  
#### Pour modifier la copie d'un argument de procédure dans le code de procédure  
  
1.  Dans la déclaration de procédure, spécifiez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pour le paramètre correspondant à l'argument.  
  
     ou  
  
     Dans le code appelant, mettez l'argument entre parenthèses dans la liste d'arguments.  Cela force [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] à passer l'argument par valeur, même si le paramètre correspondant spécifie `ByRef`.  
  
2.  Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à la copie locale de l'argument.  La valeur sous\-jacente dans le code appelant n'est pas modifiée.  
  
## Exemple  
 L'exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments.  La procédure `increase` ajoute simplement la valeur 1 à chaque élément.  La procédure `replace` assigne un nouveau tableau au paramètre `a()`, puis ajoute la valeur 1 à chaque élément.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_3.vb)]  
  
 Le premier appel `MsgBox` affiche "After increase\(n\): 11, 21, 31, 41".  Étant donné que le tableau  `n`  est un type référence,  `replace`  peut modifier ses membres, même si le mécanisme de passage est `ByVal`.  
  
 Le deuxième appel `MsgBox` affiche "After replace\(n\): 101, 201, 301".  Étant donné que `ByRef` est passé à `n`,  `replace`  peut modifier la variable  `n`  dans le code appelant et lui assigner un nouveau tableau.  Étant donné que  `n`  est un type référence,  `replace`  peut également modifier ses membres.  
  
 Vous pouvez empêcher la procédure de modifier la variable elle\-même dans le code appelant.  Consultez [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## Compilation du code  
 Lorsque vous passez une variable par référence, vous devez utiliser le mot clé `ByRef` pour spécifier ce mécanisme.  
  
 Le comportement par défaut en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] consiste à passer les arguments par valeur.  En programmation, il est toutefois conseillé d'ajouter le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) avec chaque argument déclaré.  Cela rend votre code plus lisible.  
  
## Sécurité .NET Framework  
 Permettre à une procédure de modifier la valeur sous\-jacente à un argument dans le code appelant est toujours risqué.  Vérifiez que cette valeur doit bien être modifiée et préparez\-vous à en vérifier la validité avant de l'utiliser.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)