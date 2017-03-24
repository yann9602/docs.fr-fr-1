---
title: "Dépannage des gestionnaires d’événements en Visual Basic hérités | Documents Microsoft"
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
- troubleshooting events
- inherited events
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
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
ms.openlocfilehash: 0dae6b48b1885a52b99ae3e7328340cac7b2d7d4
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Dépannage des gestionnaires d'événements hérités dans Visual Basic
Cette rubrique répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Code de gestionnaire d’événements s’exécute deux fois pour chaque appel.  
  
-   Un gestionnaire d’événements hérité ne doit pas inclure un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause. La méthode dans la classe de base est déjà associée à l’événement et se déclenche en conséquence. Supprimer le `Handles` clause de la méthode héritée.  
  
     [!code-vb[VbVbalrEvents n°&32;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Si la méthode héritée n’a pas une `Handles` (mot clé), vérifiez que votre code ne contient pas un supplément [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou d’autres méthodes qui gèrent le même événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
