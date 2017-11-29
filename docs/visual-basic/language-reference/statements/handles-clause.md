---
title: Handles, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords: Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23b3d96052ad179ea25150bb570461a9e764977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="aa09e-102">Handles, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa09e-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="aa09e-103">Déclare qu'une procédure gère un événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="aa09e-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa09e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa09e-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="aa09e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="aa09e-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="aa09e-106">Déclaration de procédure `Sub` pour la procédure qui gérera l'événement.</span><span class="sxs-lookup"><span data-stu-id="aa09e-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="aa09e-107">Liste des événements pour `proceduredeclaration` à gérer, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="aa09e-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="aa09e-108">Les événements doivent être déclenchés par la classe de base pour la classe en cours ou par un objet déclaré à l'aide du mot clé `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="aa09e-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa09e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa09e-109">Remarks</span></span>  
 <span data-ttu-id="aa09e-110">Utilisez le mot clé `Handles` à la fin d'une déclaration de procédure pour que celle-ci gère les événements déclenchés par une variable objet déclarée à l'aide du mot clé `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="aa09e-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="aa09e-111">Le mot clé `Handles` peut également être utilisé dans une classe dérivée pour gérer des événements à partir d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="aa09e-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="aa09e-112">Le mot clé `Handles` et l'instruction `AddHandler` vous permettent de spécifier que des procédures particulières gèrent des événements particuliers, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="aa09e-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="aa09e-113">Utilisez le mot clé `Handles` quand vous définissez une procédure pour indiquer qu'elle gère un événement particulier.</span><span class="sxs-lookup"><span data-stu-id="aa09e-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="aa09e-114">L'instruction `AddHandler` connecte les procédures aux événements au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="aa09e-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="aa09e-115">Pour plus d’informations, consultez [AddHandler, instruction](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa09e-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="aa09e-116">Pour les événements personnalisés, l'application appelle l'accesseur `AddHandler` de l'événement quand elle ajoute la procédure comme gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="aa09e-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="aa09e-117">Pour plus d’informations sur les événements personnalisés, consultez [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aa09e-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa09e-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa09e-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 <span data-ttu-id="aa09e-119">L'exemple suivant montre comment une classe dérivée peut utiliser l'instruction `Handles` pour gérer un événement à partir d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="aa09e-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="aa09e-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa09e-120">Example</span></span>  
 <span data-ttu-id="aa09e-121">L’exemple suivant contient deux gestionnaires d’événements de bouton pour un **Application WPF** projet.</span><span class="sxs-lookup"><span data-stu-id="aa09e-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="aa09e-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa09e-122">Example</span></span>  
 <span data-ttu-id="aa09e-123">L'exemple suivant est équivalent à l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="aa09e-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="aa09e-124">La liste `eventlist` dans la clause `Handles` contient les événements pour les deux boutons.</span><span class="sxs-lookup"><span data-stu-id="aa09e-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="aa09e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa09e-125">See Also</span></span>  
 [<span data-ttu-id="aa09e-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="aa09e-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="aa09e-127">AddHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa09e-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="aa09e-128">RemoveHandler (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa09e-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="aa09e-129">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa09e-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="aa09e-130">RaiseEvent (instruction)</span><span class="sxs-lookup"><span data-stu-id="aa09e-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [<span data-ttu-id="aa09e-131">Événements</span><span class="sxs-lookup"><span data-stu-id="aa09e-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
