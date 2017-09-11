---
title: "Comment : appeler un gestionnaire d’événements en Visual Basic | Documents Microsoft"
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
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
ms.openlocfilehash: dc0174d50c7b5f5cda9d057bce39960b3e563f4e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="71d5e-102">Comment : appeler un gestionnaire d'événements en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71d5e-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="71d5e-103">Un *événement* est une action ou une occurrence, tel qu’une souris, clic ou une limite de crédit dépassé : reconnue par un composant de programme pour lequel vous pouvez écrire du code en réponse.</span><span class="sxs-lookup"><span data-stu-id="71d5e-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="71d5e-104">Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="71d5e-105">Un gestionnaire d’événements dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="71d5e-105">An event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="71d5e-106">Toutefois, vous ne normalement l’appelez pas la même façon que les autres `Sub` procédures.</span><span class="sxs-lookup"><span data-stu-id="71d5e-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="71d5e-107">Au lieu de cela, vous identifiez la procédure comme un gestionnaire pour l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="71d5e-108">Cela avec une [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause et un [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, ou avec un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="71d5e-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="71d5e-109">À l’aide un `Handles` clause constitue la méthode par défaut pour déclarer un gestionnaire d’événements dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="71d5e-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="71d5e-110">Il s’agit de la manière dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="71d5e-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="71d5e-111">La `AddHandler` instruction convient pour déclencher des événements dynamiquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="71d5e-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="71d5e-112">Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la procédure de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="71d5e-112">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="71d5e-113">Tout code qui a accès à l’événement peut déclencher celui-ci en exécutant une [RaiseEvent, instruction](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="71d5e-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="71d5e-114">Vous pouvez associer plusieurs gestionnaires d’événements à l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="71d5e-115">Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="71d5e-116">Pour plus d’informations, consultez [événements](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="71d5e-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="71d5e-117">Pour appeler un gestionnaire d’événements à l’aide de Handles et WithEvents</span><span class="sxs-lookup"><span data-stu-id="71d5e-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="71d5e-118">Assurez-vous que l’événement est déclaré avec une [Event, instruction](../../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="71d5e-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="71d5e-119">Déclarez une variable objet au module ou la classe niveau, à l’aide de la [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="71d5e-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="71d5e-120">Le `As` pour cette variable doit spécifier la classe qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="71d5e-121">Dans la déclaration de la gestion des événements `Sub` procédure, ajoutez un [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) clause qui spécifie le `WithEvents` variable et le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="71d5e-122">Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="71d5e-122">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="71d5e-123">Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="71d5e-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="71d5e-124">L’exemple suivant définit un événement et une `WithEvents` variable qui fait référence à la classe qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="71d5e-125">La gestion des événements `Sub` procédure utilise un `Handles` clause pour spécifier la classe et l’événement qu’elle gère.</span><span class="sxs-lookup"><span data-stu-id="71d5e-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     <span data-ttu-id="71d5e-126">[!code-vb[VbVbcnProcedures n °&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="71d5e-126">[!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span></span>  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="71d5e-127">Pour appeler un gestionnaire d’événements à l’aide de AddHandler</span><span class="sxs-lookup"><span data-stu-id="71d5e-127">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="71d5e-128">Assurez-vous que l’événement est déclaré avec une `Event` instruction.</span><span class="sxs-lookup"><span data-stu-id="71d5e-128">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="71d5e-129">Exécuter un [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) connecter dynamiquement la gestion des événements `Sub` procédure avec l’événement.</span><span class="sxs-lookup"><span data-stu-id="71d5e-129">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="71d5e-130">Lorsque l’événement se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle automatiquement la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="71d5e-130">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="71d5e-131">Votre code peut utiliser un `RaiseEvent` instruction pour rendre l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="71d5e-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="71d5e-132">L’exemple suivant définit un `Sub` procédure pour gérer les <xref:System.Windows.Forms.Form.Closing>événement d’un formulaire.</xref:System.Windows.Forms.Form.Closing></span><span class="sxs-lookup"><span data-stu-id="71d5e-132">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="71d5e-133">Il utilise ensuite la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md) à associer le `catchClose` procédure comme un gestionnaire d’événements <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing></span><span class="sxs-lookup"><span data-stu-id="71d5e-133">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     <span data-ttu-id="71d5e-134">[!code-vb[VbVbcnProcedures n °&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="71d5e-134">[!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span></span>  
  
     <span data-ttu-id="71d5e-135">Vous pouvez dissocier un gestionnaire d’événements à partir d’un événement en exécutant le [RemoveHandler, instruction](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="71d5e-135">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d5e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71d5e-136">See Also</span></span>  
 <span data-ttu-id="71d5e-137">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="71d5e-137">[Procedures](./index.md) </span></span>  
<span data-ttu-id="71d5e-138"> [Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="71d5e-138"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="71d5e-139"> [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="71d5e-139"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="71d5e-140"> [AddressOf (opérateur)](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="71d5e-140"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="71d5e-141"> [Comment : créer une procédure](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="71d5e-141"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="71d5e-142"> [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="71d5e-142"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
