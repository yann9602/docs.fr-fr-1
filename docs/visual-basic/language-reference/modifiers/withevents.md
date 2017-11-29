---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords: WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.  
  
## <a name="remarks"></a>Remarques  
 Lorsqu’une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` (mot clé).  
  
 Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou le module. Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.  
  
 Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.  
  
 Vous pouvez déclarer que des variables, pas les tableaux, avec `WithEvents`.  
  
## <a name="rules"></a>Règles  
  
-   **Types d’élément.** Vous devez déclarer `WithEvents` variables comme des variables d’objet afin qu’ils puissent accepter des instances de classes. Toutefois, vous ne pouvez pas déclarer en tant que `Object`. Vous devez les déclarer en tant que la classe spécifique capable de déclencher les événements.  
  
 Le `WithEvents` modificateur peut être utilisé dans ce contexte : [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)  
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
