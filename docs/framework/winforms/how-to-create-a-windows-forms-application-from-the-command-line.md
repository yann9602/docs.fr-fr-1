---
title: "Comment : créer une application Windows Forms à partir de la ligne de commande"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="cd898-102">Comment : créer une application Windows Forms à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="cd898-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="cd898-103">Les procédures suivantes décrivent les étapes de base que vous devez effectuer pour créer et exécuter une application Windows Forms à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="cd898-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="cd898-104">Ces procédures sont très bien prises en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd898-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="cd898-105">Consultez également [procédure pas à pas : création d’un Windows Form Simple](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="cd898-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="cd898-106">Procédure</span><span class="sxs-lookup"><span data-stu-id="cd898-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="cd898-107">Pour créer le formulaire</span><span class="sxs-lookup"><span data-stu-id="cd898-107">To create the form</span></span>  
  
1.  <span data-ttu-id="cd898-108">Dans un fichier de code vide, tapez les instructions import ou using suivantes :</span><span class="sxs-lookup"><span data-stu-id="cd898-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="cd898-109">Déclarez une classe nommée `Form1` qui hérite de la classe Form.</span><span class="sxs-lookup"><span data-stu-id="cd898-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="cd898-110">Créez un constructeur par défaut pour `Form1`.</span><span class="sxs-lookup"><span data-stu-id="cd898-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="cd898-111">Vous ajouterez du code au constructeur lors d'une procédure ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cd898-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="cd898-112">Ajoutez une méthode `Main` à la classe.</span><span class="sxs-lookup"><span data-stu-id="cd898-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="cd898-113">Appliquer le <xref:System.STAThreadAttribute> à la méthode `Main` pour indiquer que votre application Windows Forms est un thread unique cloisonné.</span><span class="sxs-lookup"><span data-stu-id="cd898-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="cd898-114">Appelez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pour donner une apparence Windows XP à votre application.</span><span class="sxs-lookup"><span data-stu-id="cd898-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="cd898-115">Créez une instance du formulaire et exécutez-la.</span><span class="sxs-lookup"><span data-stu-id="cd898-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="cd898-116">Pour compiler et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="cd898-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="cd898-117">À l'invite de commandes .NET Framework, accédez au répertoire où vous avez créé la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="cd898-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="cd898-118">Compilez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="cd898-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="cd898-119">Si vous utilisez c#, tapez :`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="cd898-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="cd898-120">Si vous utilisez Visual Basic, tapez :`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="cd898-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="cd898-121">À l’invite de commandes, tapez :`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="cd898-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="cd898-122">Ajout d'un contrôle et gestion d'un événement</span><span class="sxs-lookup"><span data-stu-id="cd898-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="cd898-123">Les étapes de la procédure précédente illustrent simplement comment créer un Windows Form de base qui se compile et s'exécute.</span><span class="sxs-lookup"><span data-stu-id="cd898-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="cd898-124">La procédure suivante illustre comment créer et ajouter un contrôle au formulaire et comment gérer un événement pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="cd898-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="cd898-125">Pour plus d’informations sur les contrôles que vous pouvez ajouter aux Windows Forms, consultez [des contrôles Windows Forms](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="cd898-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="cd898-126">Outre la création d’applications Windows Forms, vous devez comprendre la programmation basée sur les événements et comment gérer l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cd898-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="cd898-127">Pour plus d’informations, consultez [création de gestionnaires d’événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), et [gestion des entrées utilisateur](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="cd898-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="cd898-128">Pour déclarer un contrôle bouton et gérer son événement click</span><span class="sxs-lookup"><span data-stu-id="cd898-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="cd898-129">Déclarez un contrôle bouton nommé `button1`.</span><span class="sxs-lookup"><span data-stu-id="cd898-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="cd898-130">Dans le constructeur, créez le bouton et définissez ses propriétés <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd898-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="cd898-131">Ajoutez le bouton au formulaire.</span><span class="sxs-lookup"><span data-stu-id="cd898-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="cd898-132">L'exemple de code suivant montre comment déclarer le contrôle bouton.</span><span class="sxs-lookup"><span data-stu-id="cd898-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="cd898-133">Créez une méthode pour gérer l'événement <xref:System.Windows.Forms.Control.Click> pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="cd898-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="cd898-134">Dans le gestionnaire d'événements click, affichez un <xref:System.Windows.Forms.MessageBox> avec le message « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="cd898-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="cd898-135">L'exemple de code suivant montre comment gérer l'événement click du contrôle bouton.</span><span class="sxs-lookup"><span data-stu-id="cd898-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="cd898-136">Associez l'événement <xref:System.Windows.Forms.Control.Click> à la méthode que vous avez créée.</span><span class="sxs-lookup"><span data-stu-id="cd898-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="cd898-137">L'exemple de code suivant montre comment associer l'événement à la méthode.</span><span class="sxs-lookup"><span data-stu-id="cd898-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="cd898-138">Compilez et exécutez l'application comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="cd898-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd898-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd898-139">Example</span></span>  
 <span data-ttu-id="cd898-140">L'exemple de code suivant constitue l'exemple complet des procédures précédentes.</span><span class="sxs-lookup"><span data-stu-id="cd898-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd898-141">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="cd898-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="cd898-142">Pour compiler le code, suivez les instructions de la procédure précédente qui expliquent comment compiler et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="cd898-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd898-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd898-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="cd898-144">Modification de l'apparence des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd898-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="cd898-145">Amélioration des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd898-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="cd898-146">Bien démarrer avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd898-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
