---
title: "Autres structures de contrôle (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a>Autres structures de contrôle (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Fournit des structures de contrôle qui vous aident à supprimer une ressource ou de réduisent le nombre de fois où que vous devez répéter une référence d’objet.  
  
## <a name="usingend-using-construction"></a>À l’aide de... À l’aide de la Construction de fin  
 Le `Using...End Using` construction établit un bloc d’instruction dans laquelle vous utilisez une ressource telle qu’une connexion SQL. Vous pouvez éventuellement acquérir la ressource avec la `Using` instruction. Lorsque vous quittez la `Using` bloc, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supprime automatiquement la ressource afin qu’il soit disponible pour un autre code à utiliser. La ressource doit être locale et supprimable. Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Avec... Se termine par la Construction  
 Le `With...End With` vous permet de spécifier une référence d’objet une fois, puis exécutez une série d’instructions qui accèdent à ses membres. Cela peut simplifier votre code et améliorer les performances car [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n’a pas de rétablir la référence pour chaque instruction qui y accède. Pour plus d’informations, consultez [avec... End With, instruction](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using (instruction)](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [With...End With (instruction)](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
