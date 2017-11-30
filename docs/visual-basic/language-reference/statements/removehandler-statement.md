---
title: RemoveHandler, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="4bd14-102">RemoveHandler, instruction</span><span class="sxs-lookup"><span data-stu-id="4bd14-102">RemoveHandler Statement</span></span>
<span data-ttu-id="4bd14-103">Supprime l’association entre un événement et un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="4bd14-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bd14-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4bd14-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4bd14-105">Parts</span></span>  
  
|<span data-ttu-id="4bd14-106">Terme</span><span class="sxs-lookup"><span data-stu-id="4bd14-106">Term</span></span>|<span data-ttu-id="4bd14-107">Définition</span><span class="sxs-lookup"><span data-stu-id="4bd14-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="4bd14-108">Le nom de l’événement géré.</span><span class="sxs-lookup"><span data-stu-id="4bd14-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="4bd14-109">Le nom de la procédure en gérant l’événement.</span><span class="sxs-lookup"><span data-stu-id="4bd14-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd14-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="4bd14-110">Remarks</span></span>  
 <span data-ttu-id="4bd14-111">Le `AddHandler` et `RemoveHandler` vous permettent de démarrer et arrêter la gestion des événements pour un événement spécifique à tout moment pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="4bd14-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bd14-112">Pour les événements personnalisés, les `RemoveHandler` instruction appelle l’événement `RemoveHandler` accesseur.</span><span class="sxs-lookup"><span data-stu-id="4bd14-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="4bd14-113">Pour plus d’informations sur les événements personnalisés, consultez [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4bd14-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd14-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bd14-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd14-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd14-115">See Also</span></span>  
 [<span data-ttu-id="4bd14-116">AddHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="4bd14-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="4bd14-117">Handles</span><span class="sxs-lookup"><span data-stu-id="4bd14-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="4bd14-118">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="4bd14-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="4bd14-119">Événements</span><span class="sxs-lookup"><span data-stu-id="4bd14-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
