---
title: "Opérateur IsTrue (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a>Opérateur IsTrue (Visual Basic)
Détermine si une expression est `True`.  
  
 Vous ne pouvez pas appeler `IsTrue` explicitement dans votre code, mais Visual Basic compilateur peut l’utiliser pour générer le code à partir de `OrElse` clauses. Si vous définissez une classe ou une structure et ensuite utiliser une variable de ce type dans un `OrElse` clause, vous devez définir `IsTrue` sur cette classe ou structure.  
  
 Le compilateur considère la `IsTrue` et `IsFalse` opérateurs comme un *paire équilibrée*. Cela signifie que si vous définissez un d’eux, vous devez également définir la deuxième.  
  
## <a name="compiler-use-of-istrue"></a>Utilisation du compilateur de IsTrue  
 Lorsque vous avez défini une classe ou structure, vous pouvez utiliser une variable de ce type dans un `For`, `If`, `Else``If`, ou `While` instruction, ou dans un `When` clause. Si vous faites cela, le compilateur requiert un opérateur qui convertit votre type en un `Boolean` valeur de façon à pouvoir tester une condition. Il recherche un opérateur adéquat dans l’ordre suivant :  
  
1.  Un opérateur de conversion étendue de votre classe ou structure à `Boolean`.  
  
2.  Un opérateur de conversion étendue de votre classe ou structure à `Boolean?`.  
  
3.  Le `IsTrue` opérateur sur votre classe ou structure.  
  
4.  Une conversion restrictive `Boolean?` qui n’implique pas de conversion de `Boolean` à `Boolean?`.  
  
5.  Un opérateur de conversion restrictive de votre classe ou structure à `Boolean`.  
  
 Si vous n’avez pas défini de conversion en `Boolean` ou `IsTrue` (opérateur), le compilateur signale une erreur.  
  
> [!NOTE]
>  Le `IsTrue` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit le plan d’une structure qui contient les définitions pour la `IsFalse` et `IsTrue` opérateurs.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [IsFalse (opérateur)](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse (opérateur)](../../../visual-basic/language-reference/operators/orelse-operator.md)
