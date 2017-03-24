---
title: WithEvents (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 708cf6fec78faf2c7a5959a3a2694d237d728882
ms.lasthandoff: 03/13/2017

---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` (mot clé).  
  
 Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module. Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.  
  
 Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.  
  
 Vous pouvez déclarer que des variables, des tableaux non — avec `WithEvents`.  
  
## <a name="rules"></a>Règles  
  
-   **Types d’élément.** Vous devez déclarer `WithEvents` variables comme des variables d’objet afin qu’ils puissent accepter des instances de classes. Toutefois, vous ne pouvez pas déclarer comme `Object`. Vous devez les déclarer comme la classe spécifique capable de déclencher les événements.  
  
 Le `WithEvents` modificateur peut être utilisé dans ce contexte : [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gère](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
