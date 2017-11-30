---
title: "New, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a>New, opérateur (Visual Basic)
Introduit un `New` clause pour créer une nouvelle instance de l’objet, spécifie une contrainte de constructeur sur un paramètre de type ou identifie une `Sub` procédure sous la forme d’un constructeur de classe.  
  
## <a name="remarks"></a>Remarques  
 Dans une déclaration ou une instruction d’assignation, un `New` clause doit spécifier une classe définie à partir de laquelle l’instance peut être créée. Cela signifie que la classe doit exposer un ou plusieurs constructeurs accessibles par le code appelant.  
  
 Vous pouvez utiliser un `New` clause dans une instruction de déclaration ou une instruction d’assignation. Lorsque l’instruction s’exécute, il appelle le constructeur approprié de la classe spécifiée, en passant les arguments que vous avez fournies. L’exemple suivant illustre cela en créant des instances d’un `Customer` classe qui possède deux constructeurs, qui ne prend aucun paramètre et une qui prend un paramètre de chaîne.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 Étant donné que les tableaux sont des classes, `New` peut créer une nouvelle instance de tableau, comme indiqué dans les exemples suivants.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 Le common language runtime (CLR) lève une <xref:System.OutOfMemoryException> erreur si la mémoire est insuffisante pour créer la nouvelle instance.  
  
> [!NOTE]
>  Le `New` est également utilisé dans les listes de paramètres de type pour spécifier que le type fourni doit exposer un constructeur sans paramètre accessible. Pour plus d’informations sur les paramètres de type et les contraintes, consultez [Type liste](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Pour créer une procédure de constructeur pour une classe, définissez le nom d’un `Sub` procédure pour le `New` (mot clé). Pour plus d’informations, consultez [durée de vie : comment les objets sont création et destruction](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 Le mot clé `New` peut être utilisé dans les contextes suivants :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.OutOfMemoryException>  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)  
 [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Durée de vie d’un objet : création et destruction des objets](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
