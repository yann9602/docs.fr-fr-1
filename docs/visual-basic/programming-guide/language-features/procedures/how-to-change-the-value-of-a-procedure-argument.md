---
title: "Comment : modifier la valeur d’un argument de la procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Comment : modifier la valeur d’un argument de la procédure (Visual Basic)
Lorsque vous appelez une procédure, chaque argument que vous fournissez correspond à un des paramètres définis dans la procédure. Dans certains cas, le code de procédure peut modifier la valeur sous-jacente à un argument dans le code appelant. Dans d’autres cas, la procédure peut modifier uniquement sa copie locale d’un argument.  
  
 Lorsque vous appelez la procédure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] effectue une copie locale de chaque argument est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Pour chaque argument passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] donne le code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.  
  
 Si l’élément sous-jacent dans le code appelant est un élément modifiable et que l’argument est passé `ByRef`, le code de procédure peut utiliser la référence directe pour modifier la valeur de l’élément dans le code appelant.  
  
## <a name="changing-the-underlying-value"></a>Modifier la valeur sous-jacente  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Pour modifier la valeur sous-jacente d’un argument de procédure dans le code appelant  
  
1.  Dans la déclaration de procédure, spécifiez [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour le paramètre correspondant à l’argument.  
  
2.  Dans le code appelant, passer un élément de programmation modifiable comme argument.  
  
3.  Dans le code appelant, ne placez pas l’argument entre parenthèses dans la liste d’arguments.  
  
4.  Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à l’élément sous-jacent dans le code appelant.  
  
 Consultez l’exemple ci-dessous pour une démonstration.  
  
## <a name="changing-local-copies"></a>Modification de Copies locales  
 Si l’élément sous-jacent dans le code appelant est un élément non modifiable, ou si l’argument est passé `ByVal`, la procédure ne peut pas modifier sa valeur dans le code appelant. Toutefois, la procédure peut modifier sa copie locale de l’argument.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Pour modifier la copie d’un argument de procédure dans le code de procédure  
  
1.  Dans la déclaration de procédure, spécifiez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pour le paramètre correspondant à l’argument.  
  
     ou  
  
     Dans le code appelant, mettez l’argument entre parenthèses dans la liste d’arguments. Cette opération force [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] à passer l’argument par valeur, même si le paramètre correspondant spécifie `ByRef`.  
  
2.  Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à la copie locale de l’argument. La valeur sous-jacente dans le code appelant n’est pas modifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments. Le `increase` procédure ajoute simplement la valeur 1 à chaque élément. Le `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute 1 à chaque élément.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ». Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal`.  
  
 La seconde `MsgBox` appel affiche « après Replace (n) : 101, 201, 301 ». Étant donné que `n` est passé `ByRef`, `replace` peut modifier la variable `n` dans le code appelant et affecter un nouveau tableau. Étant donné que `n` est un type référence, `replace` peut également modifier ses membres.  
  
 Vous pouvez empêcher la procédure de modification de la variable elle-même dans le code appelant. Consultez [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.  
  
 La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur. Toutefois, il est conseillé pour inclure la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé with chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il est toujours un risque potentiel pour autoriser une procédure modifier la valeur sous-jacente à un argument dans le code appelant. Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Guide pratique : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
