---
title: "&#39; &lt;eventname&gt;&#39; est un événement et ne peut pas être appelée directement"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="ed6d1-102">&#39; &lt;eventname&gt;&#39; est un événement et ne peut pas être appelée directement</span><span class="sxs-lookup"><span data-stu-id="ed6d1-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="ed6d1-103">' <`eventname`>' est un événement et ne peut donc pas être appelé directement.</span><span class="sxs-lookup"><span data-stu-id="ed6d1-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="ed6d1-104">Utilisez un `RaiseEvent` instruction pour déclencher un événement.</span><span class="sxs-lookup"><span data-stu-id="ed6d1-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="ed6d1-105">Un appel de procédure spécifie un événement pour le nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="ed6d1-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="ed6d1-106">Un gestionnaire d’événements est une procédure, mais l’événement lui-même est un dispositif de signalisation qui doit être déclenché et géré.</span><span class="sxs-lookup"><span data-stu-id="ed6d1-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="ed6d1-107">**ID d’erreur :** BC32022</span><span class="sxs-lookup"><span data-stu-id="ed6d1-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed6d1-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ed6d1-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ed6d1-109">Utilisez un `RaiseEvent` instruction pour signaler un événement et appeler les procédures qui le gèrent.</span><span class="sxs-lookup"><span data-stu-id="ed6d1-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6d1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed6d1-110">See Also</span></span>  
 [<span data-ttu-id="ed6d1-111">RaiseEvent (instruction)</span><span class="sxs-lookup"><span data-stu-id="ed6d1-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
