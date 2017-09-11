---
title: RaiseEvent (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
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
ms.openlocfilehash: 6a0cf1c5635335f22fddd57c7dd2baaeca6ddd23
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="raiseevent-statement"></a><span data-ttu-id="d06be-102">RaiseEvent, instruction</span><span class="sxs-lookup"><span data-stu-id="d06be-102">RaiseEvent Statement</span></span>
<span data-ttu-id="d06be-103">Déclenche un événement déclaré au niveau du module dans une classe, un formulaire ou un document.</span><span class="sxs-lookup"><span data-stu-id="d06be-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d06be-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="d06be-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d06be-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="d06be-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d06be-106">Required.</span></span> <span data-ttu-id="d06be-107">Nom de l’événement à déclencher.</span><span class="sxs-lookup"><span data-stu-id="d06be-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="d06be-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="d06be-108">Optional.</span></span> <span data-ttu-id="d06be-109">Liste délimitée par des virgules des variables, des tableaux ou des expressions.</span><span class="sxs-lookup"><span data-stu-id="d06be-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="d06be-110">Le `argumentlist` argument doit être mis entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d06be-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="d06be-111">S’il n’y a pas d’arguments, les parenthèses doivent être omis.</span><span class="sxs-lookup"><span data-stu-id="d06be-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d06be-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="d06be-112">Remarks</span></span>  
 <span data-ttu-id="d06be-113">Requis `eventname` est le nom d’un événement déclaré dans le module.</span><span class="sxs-lookup"><span data-stu-id="d06be-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="d06be-114">Il suit les conventions d’affectation des noms variables Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d06be-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="d06be-115">Si l’événement n’a pas été déclaré dans le module dans lequel il est déclenché, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="d06be-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="d06be-116">Le fragment de code suivant illustre une déclaration d’événement et une procédure dans laquelle l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="d06be-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 <span data-ttu-id="d06be-117">[!code-vb[VbVbalrEvents&#37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d06be-117">[!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="d06be-118">Vous ne pouvez pas utiliser `RaiseEvent` pour déclencher des événements qui ne sont pas explicitement déclarées dans le module.</span><span class="sxs-lookup"><span data-stu-id="d06be-118">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="d06be-119">Par exemple, tous les formulaires héritent un <xref:System.Windows.Forms.Control.Click>événement <xref:System.Windows.Forms.Form?displayProperty=fullName>, il ne peut pas être déclenché à l’aide de `RaiseEvent` dans un formulaire dérivé.</xref:System.Windows.Forms.Form?displayProperty=fullName> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="d06be-119">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=fullName>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="d06be-120">Si vous déclarez un `Click` événements dans le module formulaire, celui-ci occulte du formulaire propre <xref:System.Windows.Forms.Control.Click>événements.</xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="d06be-120">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="d06be-121">Vous pouvez toujours appeler du formulaire <xref:System.Windows.Forms.Control.Click>événement en appelant le <xref:System.Windows.Forms.Control.OnClick%2A>méthode.</xref:System.Windows.Forms.Control.OnClick%2A> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="d06be-121">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="d06be-122">Par défaut, un événement défini en Visual Basic déclenche ses gestionnaires d’événements dans l’ordre que les connexions sont établies.</span><span class="sxs-lookup"><span data-stu-id="d06be-122">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="d06be-123">Étant donné que les événements peuvent disposer de `ByRef` paramètres, un processus qui se connecte ultérieurement peut recevoir des paramètres qui ont été modifiés par un gestionnaire d’événements précédent.</span><span class="sxs-lookup"><span data-stu-id="d06be-123">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="d06be-124">Après que les gestionnaires d’événements s’exécute, le contrôle est retourné à la sous-routine qui a déclenché l’événement.</span><span class="sxs-lookup"><span data-stu-id="d06be-124">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d06be-125">Les événements non partagés ne doivent pas être déclenchés dans le constructeur de la classe dans laquelle elles sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="d06be-125">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="d06be-126">Bien que ces événements ne provoquent pas d’erreurs d’exécution, ils peuvent ne pas être interceptées par des gestionnaires d’événements associés.</span><span class="sxs-lookup"><span data-stu-id="d06be-126">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="d06be-127">Utilisez le `Shared` modificateur pour créer un événement partagé Si vous avez besoin déclencher un événement à partir d’un constructeur.</span><span class="sxs-lookup"><span data-stu-id="d06be-127">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d06be-128">Vous pouvez modifier le comportement par défaut des événements en définissant un événement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d06be-128">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="d06be-129">Pour les événements personnalisés, les `RaiseEvent` instruction appelle l’événement `RaiseEvent` accesseur.</span><span class="sxs-lookup"><span data-stu-id="d06be-129">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="d06be-130">Pour plus d’informations sur les événements personnalisés, consultez la page [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d06be-130">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d06be-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="d06be-131">Example</span></span>  
 <span data-ttu-id="d06be-132">L'exemple suivant utilise des événements pour décompter les secondes de 10 à 0.</span><span class="sxs-lookup"><span data-stu-id="d06be-132">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="d06be-133">Le code illustre plusieurs méthodes liées aux événements, des propriétés et des instructions, y compris la `RaiseEvent` instruction.</span><span class="sxs-lookup"><span data-stu-id="d06be-133">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="d06be-134">La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="d06be-134">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="d06be-135">Une source d'événement peut avoir plusieurs gestionnaires pour les événements qu'elle génère.</span><span class="sxs-lookup"><span data-stu-id="d06be-135">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="d06be-136">Quand la classe déclenche l'événement, celui-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.</span><span class="sxs-lookup"><span data-stu-id="d06be-136">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="d06be-137">L'exemple utilise également un formulaire (`Form1`) avec un bouton (`Button1`) et une zone de texte (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="d06be-137">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="d06be-138">Quand vous cliquez sur le bouton, la première zone de texte affiche un compte à rebours de 10 à 0 secondes.</span><span class="sxs-lookup"><span data-stu-id="d06be-138">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="d06be-139">Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».</span><span class="sxs-lookup"><span data-stu-id="d06be-139">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="d06be-140">Le code correspondant à `Form1` indique les états de début et de fin du formulaire.</span><span class="sxs-lookup"><span data-stu-id="d06be-140">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="d06be-141">Il contient également le code exécuté lors du déclenchement des événements.</span><span class="sxs-lookup"><span data-stu-id="d06be-141">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="d06be-142">Pour utiliser cet exemple, ouvrez un nouveau projet d’Application Windows, ajoutez un bouton nommé `Button1` et une zone de texte nommée `TextBox1` au formulaire principal, nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d06be-142">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="d06be-143">Avec le bouton droit de la forme, puis cliquez sur **afficher le Code** pour ouvrir l’éditeur de Code.</span><span class="sxs-lookup"><span data-stu-id="d06be-143">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="d06be-144">Ajouter un `WithEvents` variable dans la section des déclarations du `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="d06be-144">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 <span data-ttu-id="d06be-145">[!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d06be-145">[!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d06be-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="d06be-146">Example</span></span>  
 <span data-ttu-id="d06be-147">Ajoutez le code suivant au code pour `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d06be-147">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="d06be-148">Remplacez toute procédure en double peut-être exister, tel que `Form_Load`, ou `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="d06be-148">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 <span data-ttu-id="d06be-149">[!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d06be-149">[!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="d06be-150">Appuyez sur F5 pour exécuter l’exemple précédent, puis cliquez sur le bouton intitulé **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d06be-150">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="d06be-151">La première zone de texte commence à décompter les secondes.</span><span class="sxs-lookup"><span data-stu-id="d06be-151">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="d06be-152">Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».</span><span class="sxs-lookup"><span data-stu-id="d06be-152">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d06be-153">Le `My.Application.DoEvents` méthode ne traite pas les événements de la même manière que le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d06be-153">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="d06be-154">Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading.</span><span class="sxs-lookup"><span data-stu-id="d06be-154">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="d06be-155">Pour plus d’informations, consultez [thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="d06be-155">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06be-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d06be-156">See Also</span></span>  
 <span data-ttu-id="d06be-157">[Événements](../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="d06be-157">[Events](../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="d06be-158"> [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d06be-158"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="d06be-159"> [AddHandler (instruction)](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d06be-159"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="d06be-160"> [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d06be-160"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="d06be-161"> [Gère](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="d06be-161"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)</span></span>
