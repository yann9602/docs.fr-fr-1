---
title: "Les classes dérivées ne peuvent pas déclencher les événements de la classe de base"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="ca82a-102">Les classes dérivées ne peuvent pas déclencher les événements de la classe de base</span><span class="sxs-lookup"><span data-stu-id="ca82a-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="ca82a-103">Un événement peut être déclenché uniquement à partir de l’espace de déclaration dans lequel elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="ca82a-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="ca82a-104">Par conséquent, une classe ne peut pas déclencher d’événements à partir de toute autre classe, même si celle-ci à partir de laquelle elle est dérivée.</span><span class="sxs-lookup"><span data-stu-id="ca82a-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="ca82a-105">**ID d’erreur :** BC30029</span><span class="sxs-lookup"><span data-stu-id="ca82a-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca82a-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ca82a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ca82a-107">Déplacer le `Event` instruction ou la `RaiseEvent` instruction afin qu’ils soient dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="ca82a-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca82a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca82a-108">See Also</span></span>  
 [<span data-ttu-id="ca82a-109">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca82a-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="ca82a-110">RaiseEvent (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca82a-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
