---
title: "Autres Structures de contrôle (Visual Basic) | Documents Microsoft"
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
- statements [Visual Basic], control flow
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 639571b493037f26951bd8fbf140d7bce3244889
ms.lasthandoff: 03/13/2017

---
# <a name="other-control-structures-visual-basic"></a>Autres structures de contrôle (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fournit des structures de contrôle qui vous aident à supprimer une ressource ou de réduisent le nombre de fois où que vous devez répéter une référence d’objet.  
  
## <a name="usingend-using-construction"></a>À l’aide de... À l’aide de la Construction de fin  
 Le `Using...End Using` construction établit un bloc d’instruction dans laquelle vous utilisez une ressource telle qu’une connexion SQL. Vous pouvez éventuellement acquérir la ressource avec la `Using` instruction. Lorsque vous quittez la `Using` bloc, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supprime automatiquement la ressource afin qu’il soit disponible pour un autre code à utiliser. La ressource doit être locale et supprimable. Pour plus d’informations, consultez [instruction à l’aide de](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Avec... Mettre fin à la Construction  
 Le `With...End With` vous permet de spécifier une référence d’objet une fois, puis exécutez une série d’instructions qui accèdent à ses membres. Cela peut simplifier votre code et améliorer les performances car [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n’a pas à rétablir la référence pour chaque instruction qui y accède. Pour plus d’informations, consultez [avec... End With, instruction](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instruction using](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [With...End With (instruction)](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
