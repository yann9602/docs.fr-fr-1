---
title: "Les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords: BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="d427f-102">Les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées</span><span class="sxs-lookup"><span data-stu-id="d427f-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="d427f-103">Une variable déclarée avec le `Shared` modificateur est une variable partagée.</span><span class="sxs-lookup"><span data-stu-id="d427f-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="d427f-104">Une variable partagée identifie exactement un emplacement de stockage.</span><span class="sxs-lookup"><span data-stu-id="d427f-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="d427f-105">Une variable déclarée avec le `WithEvents` modificateur déclare que le type auquel appartient la variable gère l’ensemble de la variable déclenche des événements.</span><span class="sxs-lookup"><span data-stu-id="d427f-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="d427f-106">Lorsqu’une valeur est assignée à la variable, la propriété créée par le `WithEvents` déclaration déconnecte tout gestionnaire d’événements existant et raccorde le nouveau gestionnaire d’événements via la `Add` (méthode).</span><span class="sxs-lookup"><span data-stu-id="d427f-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="d427f-107">**ID d’erreur :** BC30594</span><span class="sxs-lookup"><span data-stu-id="d427f-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d427f-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d427f-108">To correct this error</span></span>  
  
-   <span data-ttu-id="d427f-109">Déclarez votre gestionnaire d’événements `Shared`.</span><span class="sxs-lookup"><span data-stu-id="d427f-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d427f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d427f-110">See Also</span></span>  
 [<span data-ttu-id="d427f-111">Shared</span><span class="sxs-lookup"><span data-stu-id="d427f-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="d427f-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="d427f-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
