---
title: "Déclaration et déclenchement des événements (Visual Basic) | Documents Microsoft"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
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
ms.openlocfilehash: eca112aca39bd998697d379a1705845e8f607367
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="37bb8-102">Procédure pas à pas : déclaration et déclenchement des événements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37bb8-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="37bb8-103">Cette procédure pas à pas montre comment déclarer et déclencher des événements pour une classe nommée `Widget`.</span><span class="sxs-lookup"><span data-stu-id="37bb8-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="37bb8-104">Après avoir terminé les étapes, vous souhaiterez lire la rubrique connexe, [procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), qui explique comment utiliser les événements du `Widget` objets à fournir des informations d’état dans une application.</span><span class="sxs-lookup"><span data-stu-id="37bb8-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="37bb8-105">La classe Widget</span><span class="sxs-lookup"><span data-stu-id="37bb8-105">The Widget Class</span></span>  
 <span data-ttu-id="37bb8-106">Envisageons pour l’instant que vous avez un `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="37bb8-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="37bb8-107">Votre `Widget` classe a une méthode qui peut prendre beaucoup de temps à exécuter, et vous souhaitez que votre application puisse afficher une sorte d’indicateur d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="37bb8-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="37bb8-108">Bien sûr, vous pouvez apporter les `Widget` objet affiche une boîte de dialogue de pourcentage d’achèvement, mais vous allaient être bloqués avec cette boîte de dialogue dans chaque projet dans lequel vous avez utilisé la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="37bb8-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="37bb8-109">Principe de design d’objets consiste à laisser l’application qui utilise un handle d’objet l’interface utilisateur, à moins que le but de l’objet consiste à gérer une formulaire ou boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="37bb8-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="37bb8-110">L’objectif de `Widget` consiste à effectuer d’autres tâches, il est préférable d’ajouter un `PercentDone` événement et laisser la procédure qui appelle `Widget`de méthodes gèrent que des événements et afficher l’état de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="37bb8-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="37bb8-111">Le `PercentDone` événement peut également fournir un mécanisme d’annulation de la tâche.</span><span class="sxs-lookup"><span data-stu-id="37bb8-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="37bb8-112">Pour générer l’exemple de code pour cette rubrique</span><span class="sxs-lookup"><span data-stu-id="37bb8-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="37bb8-113">Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Application Windows de projet et créez un formulaire nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="37bb8-113">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="37bb8-114">Ajoutez deux boutons et une étiquette à `Form1`.</span><span class="sxs-lookup"><span data-stu-id="37bb8-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="37bb8-115">Nommez les objets comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="37bb8-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="37bb8-116">Objet</span><span class="sxs-lookup"><span data-stu-id="37bb8-116">Object</span></span>|<span data-ttu-id="37bb8-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="37bb8-117">Property</span></span>|<span data-ttu-id="37bb8-118">Paramètre</span><span class="sxs-lookup"><span data-stu-id="37bb8-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="37bb8-119">Tâche de démarrage</span><span class="sxs-lookup"><span data-stu-id="37bb8-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="37bb8-120">Annuler</span><span class="sxs-lookup"><span data-stu-id="37bb8-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="37bb8-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="37bb8-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="37bb8-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="37bb8-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="37bb8-123">Sur le **projet** menu, choisissez **ajouter une classe** pour ajouter une classe nommée `Widget.vb` au projet.</span><span class="sxs-lookup"><span data-stu-id="37bb8-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="37bb8-124">Pour déclarer un événement pour la classe Widget</span><span class="sxs-lookup"><span data-stu-id="37bb8-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="37bb8-125">Utilisez le `Event` (mot clé) pour déclarer un événement dans la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="37bb8-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="37bb8-126">Notez qu’un événement peut avoir `ByVal` et `ByRef` arguments, en tant que `Widget`de `PercentDone` illustre l’événement :</span><span class="sxs-lookup"><span data-stu-id="37bb8-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     <span data-ttu-id="37bb8-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="37bb8-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span></span>  
  
 <span data-ttu-id="37bb8-128">Lorsque l’objet appelant reçoit un `PercentDone` événement, le `Percent` argument contient le pourcentage de la tâche est terminée.</span><span class="sxs-lookup"><span data-stu-id="37bb8-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="37bb8-129">Le `Cancel` argument peut être défini sur `True` pour annuler la méthode ayant déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="37bb8-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37bb8-130">Vous pouvez déclarer des arguments d’événement comme arguments de procédures, avec les exceptions suivantes : les événements ne peut pas avoir `Optional` ou `ParamArray` arguments et les événements n’ont pas de valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="37bb8-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="37bb8-131">Le `PercentDone` événement est déclenché par le `LongTask` procédé de la `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="37bb8-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="37bb8-132">`LongTask`prend deux arguments : la durée pendant laquelle la méthode prétend être active et l’intervalle minimal avant `LongTask` suspendue pour déclencher le `PercentDone` événement.</span><span class="sxs-lookup"><span data-stu-id="37bb8-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="37bb8-133">Pour déclencher l’événement PercentDone</span><span class="sxs-lookup"><span data-stu-id="37bb8-133">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="37bb8-134">Pour simplifier l’accès à la `Timer` propriété utilisée par cette classe, ajoutez une `Imports` en haut de la section des déclarations de votre module de classe, au-dessus de la `Class Widget` instruction.</span><span class="sxs-lookup"><span data-stu-id="37bb8-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     <span data-ttu-id="37bb8-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="37bb8-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span></span>  
  
2.  <span data-ttu-id="37bb8-136">Ajoutez le code suivant à la classe `Widget` :</span><span class="sxs-lookup"><span data-stu-id="37bb8-136">Add the following code to the `Widget` class:</span></span>  
  
     <span data-ttu-id="37bb8-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="37bb8-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span></span>  
  
 <span data-ttu-id="37bb8-138">Lorsque votre application appelle la `LongTask` (méthode), la `Widget` classe déclenche le `PercentDone` événement chaque `MinimumInterval` secondes.</span><span class="sxs-lookup"><span data-stu-id="37bb8-138">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="37bb8-139">Retourne l’événement `LongTask` vérifie si le `Cancel` argument a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="37bb8-139">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="37bb8-140">Quelques mises en garde sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="37bb8-140">A few disclaimers are necessary here.</span></span> <span data-ttu-id="37bb8-141">Pour plus de simplicité, le `LongTask` procédure suppose que vous connaissez à l’avance combien de temps prendra la tâche.</span><span class="sxs-lookup"><span data-stu-id="37bb8-141">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="37bb8-142">C’est presque jamais le cas.</span><span class="sxs-lookup"><span data-stu-id="37bb8-142">This is almost never the case.</span></span> <span data-ttu-id="37bb8-143">Il peut être difficile de diviser les tâches en segments de même longueur et souvent essentiel pour les utilisateurs est simplement la quantité de temps qui s’écoule avant une indication que quelque chose qui se passe.</span><span class="sxs-lookup"><span data-stu-id="37bb8-143">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="37bb8-144">Vous avez peut-être remarqué une autre faille dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="37bb8-144">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="37bb8-145">Le `Timer` propriété renvoie le nombre de secondes écoulées depuis minuit ; par conséquent, l’application reste bloquée si elle est démarrée juste avant minuit.</span><span class="sxs-lookup"><span data-stu-id="37bb8-145">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="37bb8-146">Une approche plus prudente pour mesurer le temps serait prendre en considération les conditions de limite telles que cela, ou les éviter, à l’aide des propriétés telles que `Now`.</span><span class="sxs-lookup"><span data-stu-id="37bb8-146">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="37bb8-147">Maintenant que la `Widget` classe peut déclencher des événements, vous pouvez passer à la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="37bb8-147">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="37bb8-148">[Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) montre comment utiliser `WithEvents` pour associer un gestionnaire d’événements avec le `PercentDone` événement.</span><span class="sxs-lookup"><span data-stu-id="37bb8-148">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bb8-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37bb8-149">See Also</span></span>  
 <span data-ttu-id="37bb8-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span><span class="sxs-lookup"><span data-stu-id="37bb8-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span></span>   
 <span data-ttu-id="37bb8-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="37bb8-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span></span>   
<span data-ttu-id="37bb8-152"> [Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span><span class="sxs-lookup"><span data-stu-id="37bb8-152"> [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span></span>  
<span data-ttu-id="37bb8-153"> [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="37bb8-153"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
