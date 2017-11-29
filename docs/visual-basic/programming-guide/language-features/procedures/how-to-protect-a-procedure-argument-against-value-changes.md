---
title: "Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)"
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
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)
Si une procédure déclare un paramètre comme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] donne le code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant. Cela permet à la procédure pour modifier la valeur sous-jacente à l’argument dans le code appelant. Dans certains cas, le code appelant souhaiteriez pour vous protéger contre une telle modification.  
  
 Vous pouvez toujours protéger un argument de modification en déclarant le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la procédure. Si vous souhaitez être en mesure de modifier un argument donné dans certains cas, mais pas d’autres, vous pouvez la déclarer `ByRef` et laisser le code appelant déterminer le mécanisme de passage dans chaque appel. Cela en mettant l’argument correspondant entre parenthèses pour le passer par valeur, ou en mettant ne pas entre parenthèses pour le passer par référence. Pour plus d’informations, consultez [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments. Le `increase` procédure ajoute simplement la valeur 1 à chaque élément. Le `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute 1 à chaque élément. Toutefois, la réaffectation n’affecte pas la variable tableau sous-jacente dans le code appelant.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ». Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal`.  
  
 La seconde `MsgBox` appel affiche « après Replace (n) : 11, 21, 31, 41 ». Étant donné que `n` est passé `ByVal`, `replace` ne peut pas modifier la variable `n` dans le code appelant en lui assignant un nouveau tableau. Lorsque `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, il perd la référence à `n` transmis par le code appelant. Lorsqu’il modifie les membres de `a`, seul le tableau local `k` est affectée. Par conséquent, `replace` n’incrémente pas les valeurs du tableau `n` dans le code appelant.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur. Toutefois, il est conseillé pour inclure la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé with chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
