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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f64395975821226d42664bbf78b04120d49a38bc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="6fd94-102">Dépannage des gestionnaires d'événements hérités dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fd94-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="6fd94-103">Cette rubrique répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités.</span><span class="sxs-lookup"><span data-stu-id="6fd94-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="6fd94-104">Procédures</span><span class="sxs-lookup"><span data-stu-id="6fd94-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="6fd94-105">Code de gestionnaire d’événements s’exécute deux fois pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="6fd94-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="6fd94-106">Un gestionnaire d’événements hérité ne doit pas inclure un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span><span class="sxs-lookup"><span data-stu-id="6fd94-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="6fd94-107">La méthode dans la classe de base est déjà associée à l’événement et se déclenche en conséquence.</span><span class="sxs-lookup"><span data-stu-id="6fd94-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="6fd94-108">Supprimer le `Handles` clause de la méthode héritée.</span><span class="sxs-lookup"><span data-stu-id="6fd94-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     <span data-ttu-id="6fd94-109">[!code-vb[VbVbalrEvents n°&32;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6fd94-109">[!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span></span>  
  
-   <span data-ttu-id="6fd94-110">Si la méthode héritée n’a pas une `Handles` (mot clé), vérifiez que votre code ne contient pas un supplément [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou d’autres méthodes qui gèrent le même événement.</span><span class="sxs-lookup"><span data-stu-id="6fd94-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd94-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fd94-111">See Also</span></span>  
 [<span data-ttu-id="6fd94-112">Événements</span><span class="sxs-lookup"><span data-stu-id="6fd94-112">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
