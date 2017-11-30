---
title: "Déclaration et déclenchement des événements (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf75cfba5102be5d837af385e2d3578f78a03c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="2436f-102">Procédure pas à pas : déclaration et déclenchement des événements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2436f-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="2436f-103">Cette procédure pas à pas montre comment déclarer et déclencher des événements pour une classe nommée `Widget`.</span><span class="sxs-lookup"><span data-stu-id="2436f-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="2436f-104">Après avoir terminé les étapes, vous pouvez souhaiter lire la rubrique connexe, [procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), qui montre comment utiliser les événements du `Widget` objets pour fournir des informations d’état dans une application.</span><span class="sxs-lookup"><span data-stu-id="2436f-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="2436f-105">La classe Widget</span><span class="sxs-lookup"><span data-stu-id="2436f-105">The Widget Class</span></span>  
 <span data-ttu-id="2436f-106">Supposons pour le moment que vous avez un `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="2436f-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="2436f-107">Votre `Widget` classe possède une méthode qui peut prendre beaucoup de temps à exécuter, et vous souhaitez que votre application peut placer une sorte d’indicateur de fin.</span><span class="sxs-lookup"><span data-stu-id="2436f-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="2436f-108">Bien entendu, vous pouvez apporter les `Widget` objet affiche une boîte de dialogue de pourcentage achevé, mais vous devez se bloquer avec cette boîte de dialogue dans chaque projet dans lequel vous avez utilisé la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="2436f-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="2436f-109">Un principe de conception de l’objet consiste à laisser l’application qui utilise un handle d’objet de l’interface utilisateur, sauf si le but de l’objet consiste à gérer une formulaire ou boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2436f-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="2436f-110">L’objectif de `Widget` consiste à effectuer d’autres tâches, il est préférable d’ajouter un `PercentDone` événement et permettent la procédure qui appelle `Widget`de méthodes gèrent que des événements et afficher l’état de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="2436f-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="2436f-111">Le `PercentDone` événement peut également fournir un mécanisme d’annulation de la tâche.</span><span class="sxs-lookup"><span data-stu-id="2436f-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="2436f-112">Pour générer l’exemple de code pour cette rubrique</span><span class="sxs-lookup"><span data-stu-id="2436f-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="2436f-113">Ouvrez une nouvelle [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Application Windows de projet et créez un formulaire nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2436f-113">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="2436f-114">Ajoutez deux boutons et une étiquette à `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2436f-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="2436f-115">Nommez les objets de la façon indiquée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2436f-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="2436f-116">Objet</span><span class="sxs-lookup"><span data-stu-id="2436f-116">Object</span></span>|<span data-ttu-id="2436f-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="2436f-117">Property</span></span>|<span data-ttu-id="2436f-118">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2436f-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="2436f-119">Tâche de démarrage</span><span class="sxs-lookup"><span data-stu-id="2436f-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="2436f-120">Annuler</span><span class="sxs-lookup"><span data-stu-id="2436f-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="2436f-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="2436f-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="2436f-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="2436f-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="2436f-123">Sur le **projet** menu, choisissez **ajouter une classe** pour ajouter une classe nommée `Widget.vb` au projet.</span><span class="sxs-lookup"><span data-stu-id="2436f-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="2436f-124">Pour déclarer un événement pour la classe Widget</span><span class="sxs-lookup"><span data-stu-id="2436f-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="2436f-125">Utilisez le `Event` (mot clé) pour déclarer un événement dans le `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="2436f-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="2436f-126">Notez qu’un événement peut avoir `ByVal` et `ByRef` arguments, en tant que `Widget`de `PercentDone` illustre l’événement :</span><span class="sxs-lookup"><span data-stu-id="2436f-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 <span data-ttu-id="2436f-127">Lorsque l’objet appelant reçoit un `PercentDone` événement, le `Percent` argument contient le pourcentage de la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="2436f-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="2436f-128">Le `Cancel` argument peut être défini sur `True` pour annuler la méthode qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="2436f-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2436f-129">Vous pouvez déclarer des arguments d’événement comme arguments de procédures, avec les exceptions suivantes : les événements ne peut pas avoir `Optional` ou `ParamArray` arguments et les événements n’ont pas de valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="2436f-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="2436f-130">Le `PercentDone` événement est déclenché par le `LongTask` méthode de la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="2436f-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="2436f-131">`LongTask`accepte deux arguments : la durée pendant laquelle la méthode prétend être active et l’intervalle minimal avant `LongTask` suspendue pour déclencher le `PercentDone` événement.</span><span class="sxs-lookup"><span data-stu-id="2436f-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="2436f-132">Pour déclencher l’événement PercentDone</span><span class="sxs-lookup"><span data-stu-id="2436f-132">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="2436f-133">Pour simplifier l’accès à la `Timer` propriété utilisée par cette classe, ajoutez une `Imports` en haut de la section des déclarations de votre module de classe, au-dessus de la `Class Widget` instruction.</span><span class="sxs-lookup"><span data-stu-id="2436f-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  <span data-ttu-id="2436f-134">Ajoutez le code suivant à la classe `Widget` :</span><span class="sxs-lookup"><span data-stu-id="2436f-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 <span data-ttu-id="2436f-135">Lorsque votre application appelle la `LongTask` (méthode), la `Widget` classe déclenche le `PercentDone` événement chaque `MinimumInterval` secondes.</span><span class="sxs-lookup"><span data-stu-id="2436f-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="2436f-136">Retourne l’événement `LongTask` vérifie si le `Cancel` argument a été défini sur `True`.</span><span class="sxs-lookup"><span data-stu-id="2436f-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="2436f-137">Quelques mises en garde sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2436f-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="2436f-138">Par souci de simplicité, le `LongTask` procédure suppose que vous connaissez à l’avance prendra la durée pendant laquelle la tâche.</span><span class="sxs-lookup"><span data-stu-id="2436f-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="2436f-139">Cela n’est presque jamais la casse.</span><span class="sxs-lookup"><span data-stu-id="2436f-139">This is almost never the case.</span></span> <span data-ttu-id="2436f-140">Peut être difficile de diviser les tâches en segments de taille égale, et souvent essentiel pour les utilisateurs est simplement la quantité de temps qui s’écoule avant de pouvoir l’indication que quelque chose se produit.</span><span class="sxs-lookup"><span data-stu-id="2436f-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="2436f-141">Dans cet exemple, vous avez remarqué une autre faille.</span><span class="sxs-lookup"><span data-stu-id="2436f-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="2436f-142">Le `Timer` propriété retourne le nombre de secondes écoulées depuis minuit ; par conséquent, l’application se bloque si elle est démarrée juste avant minuit.</span><span class="sxs-lookup"><span data-stu-id="2436f-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="2436f-143">Une approche plus prudente pour mesurer le temps permet de prendre en considération les conditions de limite comme celui-ci, ou les éviter, à l’aide des propriétés telles que `Now`.</span><span class="sxs-lookup"><span data-stu-id="2436f-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="2436f-144">Maintenant que la `Widget` classe peut déclencher des événements, vous pouvez passer à la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="2436f-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="2436f-145">[Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) montre comment utiliser `WithEvents` pour associer un gestionnaire d’événements avec le `PercentDone` événement.</span><span class="sxs-lookup"><span data-stu-id="2436f-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2436f-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2436f-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [<span data-ttu-id="2436f-147">Procédure pas à pas : gestion des événements</span><span class="sxs-lookup"><span data-stu-id="2436f-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [<span data-ttu-id="2436f-148">Événements</span><span class="sxs-lookup"><span data-stu-id="2436f-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
