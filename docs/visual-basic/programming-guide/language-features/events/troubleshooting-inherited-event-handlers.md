---
title: "Dépannage des gestionnaires d'événements hérités dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="2e893-102">Dépannage des gestionnaires d'événements hérités dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e893-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="2e893-103">Cette rubrique répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités.</span><span class="sxs-lookup"><span data-stu-id="2e893-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2e893-104">Procédures</span><span class="sxs-lookup"><span data-stu-id="2e893-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="2e893-105">Code de gestionnaire d’événements s’exécute deux fois pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="2e893-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="2e893-106">Un gestionnaire d’événements hérité ne doit pas inclure un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span><span class="sxs-lookup"><span data-stu-id="2e893-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="2e893-107">La méthode dans la classe de base est déjà associée à l’événement et se déclenche en conséquence.</span><span class="sxs-lookup"><span data-stu-id="2e893-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="2e893-108">Supprimer le `Handles` clause de la méthode héritée.</span><span class="sxs-lookup"><span data-stu-id="2e893-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="2e893-109">Si la méthode héritée n’a pas un `Handles` (mot clé), vérifiez que votre code ne contient pas un fichier extra [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou d’autres méthodes qui gèrent le même événement.</span><span class="sxs-lookup"><span data-stu-id="2e893-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e893-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e893-110">See Also</span></span>  
 [<span data-ttu-id="2e893-111">Événements</span><span class="sxs-lookup"><span data-stu-id="2e893-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
