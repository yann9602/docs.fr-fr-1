---
title: "La gestion des événements (Visual Basic) | Documents Microsoft"
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
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
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
ms.openlocfilehash: b4ad77b3b0236e762fc17b8aba9d34108c8d75b5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="f4500-102">Procédure pas à pas : gestion des événements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4500-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="f4500-103">Il s’agit de la deuxième des deux rubriques qui montrent comment utiliser des événements.</span><span class="sxs-lookup"><span data-stu-id="f4500-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="f4500-104">La première rubrique, [procédure pas à pas : déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), montre comment déclarer et déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="f4500-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="f4500-105">Cette section utilise le formulaire et la classe à partir de cette procédure pas à pas pour montrer comment gérer les événements lorsqu’ils se produisent.</span><span class="sxs-lookup"><span data-stu-id="f4500-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="f4500-106">Le `Widget` exemple de classe utilise des instructions de gestion des événements traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="f4500-106">The `Widget` class example uses traditional event-handling statements.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="f4500-107">fournit d’autres techniques pour l’utilisation des événements.</span><span class="sxs-lookup"><span data-stu-id="f4500-107"> provides other techniques for working with events.</span></span> <span data-ttu-id="f4500-108">En guise d’exercice, vous pouvez modifier cet exemple montre comment utiliser le `AddHandler` et `Handles` instructions.</span><span class="sxs-lookup"><span data-stu-id="f4500-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="f4500-109">Pour gérer l’événement PercentDone de la classe Widget</span><span class="sxs-lookup"><span data-stu-id="f4500-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="f4500-110">Placez le code suivant dans `Form1`:</span><span class="sxs-lookup"><span data-stu-id="f4500-110">Place the following code in `Form1`:</span></span>  
  
     <span data-ttu-id="f4500-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span></span>  
  
     <span data-ttu-id="f4500-112">Le `WithEvents` (mot clé) Spécifie que la variable `mWidget` est utilisée pour gérer les événements d’un objet.</span><span class="sxs-lookup"><span data-stu-id="f4500-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="f4500-113">Vous spécifiez le type d’objet en fournissant le nom de la classe à partir duquel l’objet sera créé.</span><span class="sxs-lookup"><span data-stu-id="f4500-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="f4500-114">La variable `mWidget` est déclarée dans `Form1` car `WithEvents` variables doivent être de niveau classe.</span><span class="sxs-lookup"><span data-stu-id="f4500-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="f4500-115">Cela est vrai quel que soit le type de classe que vous les placez dans.</span><span class="sxs-lookup"><span data-stu-id="f4500-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="f4500-116">La variable `mblnCancel` est utilisée pour annuler le `LongTask` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f4500-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="f4500-117">Écriture de Code pour gérer un événement</span><span class="sxs-lookup"><span data-stu-id="f4500-117">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="f4500-118">Dès que vous déclarez une variable à l’aide `WithEvents`, le nom de la variable s’affiche dans la liste déroulante gauche de la classe **éditeur de Code**.</span><span class="sxs-lookup"><span data-stu-id="f4500-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="f4500-119">Lorsque vous sélectionnez `mWidget`, le `Widget` événements de la classe apparaissent dans la liste déroulante à droite.</span><span class="sxs-lookup"><span data-stu-id="f4500-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="f4500-120">Sélection d’un événement affiche la procédure d’événement correspondante, avec le préfixe `mWidget` et un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="f4500-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="f4500-121">Toutes les procédures d’événement associés à une `WithEvents` variable portent le nom de variable comme préfixe.</span><span class="sxs-lookup"><span data-stu-id="f4500-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="f4500-122">Pour gérer un événement</span><span class="sxs-lookup"><span data-stu-id="f4500-122">To handle an event</span></span>  
  
1.  <span data-ttu-id="f4500-123">Sélectionnez `mWidget` dans la liste déroulante dans le **éditeur de Code**.</span><span class="sxs-lookup"><span data-stu-id="f4500-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="f4500-124">Sélectionnez le `PercentDone` événement dans la liste déroulante à droite.</span><span class="sxs-lookup"><span data-stu-id="f4500-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="f4500-125">Le **éditeur de Code** ouvre le `mWidget_PercentDone` procédure d’événement.</span><span class="sxs-lookup"><span data-stu-id="f4500-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4500-126">Le **éditeur de Code** est utile, mais pas obligatoire, pour l’insertion de nouveaux gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="f4500-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="f4500-127">Dans cette procédure pas à pas, il est plus rapide de copier simplement les gestionnaires d’événements directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f4500-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="f4500-128">Ajoutez le code suivant au gestionnaire d'événements `mWidget_PercentDone` :</span><span class="sxs-lookup"><span data-stu-id="f4500-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     <span data-ttu-id="f4500-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span></span>  
  
     <span data-ttu-id="f4500-130">Chaque fois que le `PercentDone` événement est déclenché, la procédure événementielle affiche le pourcentage d’achèvement dans un `Label` contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4500-130">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="f4500-131">Le `DoEvents` méthode autorise l’étiquette soit repeinte et donne également à l’utilisateur la possibilité de cliquer sur le **Annuler** bouton.</span><span class="sxs-lookup"><span data-stu-id="f4500-131">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="f4500-132">Ajoutez le code suivant pour le `Button2_Click` Gestionnaire d’événements :</span><span class="sxs-lookup"><span data-stu-id="f4500-132">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     <span data-ttu-id="f4500-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span></span>  
  
 <span data-ttu-id="f4500-134">Si l’utilisateur clique sur le **Annuler** tout en `LongTask` est en cours d’exécution, le `Button2_Click` événement est exécuté dès que la `DoEvents` instruction permet le traitement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="f4500-134">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="f4500-135">La variable de niveau classe `mblnCancel` est défini sur `True`et le `mWidget_PercentDone` événement, puis le teste et définit les `ByRef Cancel` l’argument de `True`.</span><span class="sxs-lookup"><span data-stu-id="f4500-135">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="f4500-136">Connexion d’une Variable WithEvents à un objet</span><span class="sxs-lookup"><span data-stu-id="f4500-136">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="f4500-137">`Form1`est désormais configuré pour gérer un `Widget` événements de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f4500-137">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="f4500-138">Ne reste qu’à trouver un `Widget` quelque part.</span><span class="sxs-lookup"><span data-stu-id="f4500-138">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="f4500-139">Lorsque vous déclarez une variable `WithEvents` au moment du design, aucun objet ne lui n’est associé.</span><span class="sxs-lookup"><span data-stu-id="f4500-139">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="f4500-140">A `WithEvents` variable est qu’une variable objet parmi les autres.</span><span class="sxs-lookup"><span data-stu-id="f4500-140">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="f4500-141">Vous devez créer un objet et lui assigner une référence à l’aide du `WithEvents` variable.</span><span class="sxs-lookup"><span data-stu-id="f4500-141">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="f4500-142">Pour créer un objet et lui assigner une référence à celui-ci</span><span class="sxs-lookup"><span data-stu-id="f4500-142">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="f4500-143">Sélectionnez **(Form1 Events)** dans la liste déroulante dans le **éditeur de Code**.</span><span class="sxs-lookup"><span data-stu-id="f4500-143">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="f4500-144">Sélectionnez le `Load` événement dans la liste déroulante à droite.</span><span class="sxs-lookup"><span data-stu-id="f4500-144">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="f4500-145">Le **éditeur de Code** ouvre le `Form1_Load` procédure d’événement.</span><span class="sxs-lookup"><span data-stu-id="f4500-145">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="f4500-146">Ajoutez le code suivant pour le `Form1_Load` procédure d’événement pour créer le `Widget`:</span><span class="sxs-lookup"><span data-stu-id="f4500-146">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     <span data-ttu-id="f4500-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span></span>  
  
 <span data-ttu-id="f4500-148">Lorsque ce code s’exécute, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] crée un `Widget` de l’objet et associe ses événements aux procédures événementielles avec `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="f4500-148">When this code executes, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="f4500-149">Partir de ce point, chaque fois que le `Widget` déclenche son `PercentDone` événement, le `mWidget_PercentDone` procédure événementielle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="f4500-149">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="f4500-150">Pour appeler la méthode LongTask</span><span class="sxs-lookup"><span data-stu-id="f4500-150">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="f4500-151">Ajoutez le code suivant au gestionnaire d'événements `Button1_Click` :</span><span class="sxs-lookup"><span data-stu-id="f4500-151">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     <span data-ttu-id="f4500-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span></span>  
  
 <span data-ttu-id="f4500-153">Avant du `LongTask` méthode est appelée, l’étiquette qu’affiche le pourcentage d’achèvement doit être initialisé et niveau de la classe `Boolean` indicateur pour l’annulation de la méthode doit être définie sur `False`.</span><span class="sxs-lookup"><span data-stu-id="f4500-153">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="f4500-154">`LongTask`est appelé avec une durée de la tâche étant de 12,2 secondes.</span><span class="sxs-lookup"><span data-stu-id="f4500-154">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="f4500-155">Le `PercentDone` événement est déclenché une fois tous les tiers de seconde.</span><span class="sxs-lookup"><span data-stu-id="f4500-155">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="f4500-156">Chaque fois que l’événement est déclenché, le `mWidget_PercentDone` procédure événementielle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="f4500-156">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="f4500-157">Lors de la `LongTask` terminée, `mblnCancel` est testé pour voir si `LongTask` s’est terminée normalement, ou si elle s’est arrêté car `mblnCancel` a été défini sur `True`.</span><span class="sxs-lookup"><span data-stu-id="f4500-157">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="f4500-158">Le pourcentage d’achèvement est mis à jour uniquement dans le premier cas.</span><span class="sxs-lookup"><span data-stu-id="f4500-158">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="f4500-159">Pour exécuter le programme</span><span class="sxs-lookup"><span data-stu-id="f4500-159">To run the program</span></span>  
  
1.  <span data-ttu-id="f4500-160">Appuyez sur F5 pour passer le projet en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f4500-160">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="f4500-161">Cliquez sur le **démarrer la tâche** bouton.</span><span class="sxs-lookup"><span data-stu-id="f4500-161">Click the **Start Task** button.</span></span> <span data-ttu-id="f4500-162">Chaque fois que le `PercentDone` événement est déclenché, l’étiquette est mise à jour avec le pourcentage de la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="f4500-162">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="f4500-163">Cliquez sur le **Annuler** bouton Arrêter la tâche.</span><span class="sxs-lookup"><span data-stu-id="f4500-163">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="f4500-164">Notez que l’apparence de la **Annuler** bouton ne change pas immédiatement lorsque vous cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="f4500-164">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="f4500-165">Le `Click` événement ne peut pas se produire jusqu'à ce que la `My.Application.DoEvents` instruction permet le traitement des événements.</span><span class="sxs-lookup"><span data-stu-id="f4500-165">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4500-166">Le `My.Application.DoEvents` méthode ne traite pas les événements de la même manière que le formulaire.</span><span class="sxs-lookup"><span data-stu-id="f4500-166">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="f4500-167">Par exemple, dans cette procédure pas à pas, vous devez cliquer sur le **Annuler** bouton deux fois.</span><span class="sxs-lookup"><span data-stu-id="f4500-167">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="f4500-168">Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading.</span><span class="sxs-lookup"><span data-stu-id="f4500-168">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="f4500-169">Pour plus d’informations, consultez [thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="f4500-169">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="f4500-170">Il peut s’avérer intéressant d’exécuter le programme en appuyant sur F11 pour parcourir le code une ligne à la fois.</span><span class="sxs-lookup"><span data-stu-id="f4500-170">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="f4500-171">Vous pouvez voir clairement comment l’exécution passe `LongTask`et puis repasse brièvement dans `Form1` chaque fois que le `PercentDone` événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="f4500-171">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="f4500-172">Que se passerait-il si, alors que l’exécution a été dans le code de `Form1`, la `LongTask` méthode était de nouveau appelée ?</span><span class="sxs-lookup"><span data-stu-id="f4500-172">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="f4500-173">Au pire, un débordement de pile peut se produire si `LongTask` appelées chaque fois que l’événement a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="f4500-173">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="f4500-174">Vous pouvez provoquer la variable `mWidget` pour gérer les événements d’un autre `Widget` objet en assignant une référence à la nouvelle `Widget` à `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="f4500-174">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="f4500-175">En fait, vous pouvez rendre le code dans `Button1_Click` cette opération chaque fois que vous cliquez sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="f4500-175">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="f4500-176">Pour gérer les événements pour un autre objet widget</span><span class="sxs-lookup"><span data-stu-id="f4500-176">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="f4500-177">Ajoutez la ligne suivante de code pour le `Button1_Click` procédure, juste avant la ligne `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="f4500-177">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     <span data-ttu-id="f4500-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4500-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span></span>  
  
 <span data-ttu-id="f4500-179">Le code ci-dessus crée un `Widget` chaque fois que le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="f4500-179">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="f4500-180">Dès que la `LongTask` méthode se termine, la référence à la `Widget` est libéré et le `Widget` est détruit.</span><span class="sxs-lookup"><span data-stu-id="f4500-180">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="f4500-181">A `WithEvents` variable peut contenir uniquement une référence d’objet à la fois, donc si vous affectez une autre `Widget` objet `mWidget`, du précédent `Widget` événements d’objet seront n’est plus gérées.</span><span class="sxs-lookup"><span data-stu-id="f4500-181">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="f4500-182">Si `mWidget` est la seule variable objet qui contient une référence à l’ancien `Widget`, l’objet est détruit.</span><span class="sxs-lookup"><span data-stu-id="f4500-182">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="f4500-183">Si vous souhaitez gérer des événements de plusieurs `Widget` objets, utilisez la `AddHandler` instruction de traitement des événements de chaque objet séparément.</span><span class="sxs-lookup"><span data-stu-id="f4500-183">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4500-184">Vous pouvez déclarer autant `WithEvents` les variables que vous avez besoin, mais les tableaux de `WithEvents` variables ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f4500-184">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4500-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4500-185">See Also</span></span>  
 <span data-ttu-id="f4500-186">[Procédure pas à pas : Déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span><span class="sxs-lookup"><span data-stu-id="f4500-186">[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span></span>  
<span data-ttu-id="f4500-187"> [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="f4500-187"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
