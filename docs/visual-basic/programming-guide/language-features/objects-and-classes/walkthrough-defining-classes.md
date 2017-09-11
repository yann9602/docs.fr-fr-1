---
title: "Définition des Classes (Visual Basic) | Documents Microsoft"
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: 5b470b8ba9b60dfb1cd1bbb207e02217f5311c27
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="f6183-102">Procédure pas à pas : définition des classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6183-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="f6183-103">Cette procédure pas à pas montre comment définir des classes que vous pouvez ensuite utiliser pour créer des objets.</span><span class="sxs-lookup"><span data-stu-id="f6183-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="f6183-104">Il vous montre comment ajouter des propriétés et des méthodes à la nouvelle classe et vous montre comment initialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="f6183-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="f6183-105">Pour définir une classe</span><span class="sxs-lookup"><span data-stu-id="f6183-105">To define a class</span></span>  
  
1.  <span data-ttu-id="f6183-106">Créer un projet en cliquant sur **nouveau projet** sur la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="f6183-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="f6183-107">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f6183-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f6183-108">Sélectionnez Application Windows dans la liste des [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour afficher le nouveau projet de modèles de projet.</span><span class="sxs-lookup"><span data-stu-id="f6183-108">Select Windows Application from the list of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="f6183-109">Ajoutez une nouvelle classe au projet en cliquant sur **ajouter une classe** sur la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="f6183-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="f6183-110">Le **ajouter un nouvel élément** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f6183-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f6183-111">Sélectionnez le **classe** modèle.</span><span class="sxs-lookup"><span data-stu-id="f6183-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="f6183-112">Nommez la nouvelle classe `UserNameInfo.vb`, puis cliquez sur **ajouter** pour afficher le code de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="f6183-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     <span data-ttu-id="f6183-113">[!code-vb[VbVbalrOOP n °&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-113">[!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6183-114">Vous pouvez utiliser la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **éditeur de Code** pour ajouter une classe à votre formulaire de démarrage en tapant le `Class` (mot clé), suivie du nom de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="f6183-114">You can use the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="f6183-115">Le **éditeur de Code** fournit un correspondant `End Class` instruction pour vous.</span><span class="sxs-lookup"><span data-stu-id="f6183-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="f6183-116">Définissez un champ privé pour la classe en ajoutant le code suivant entre les `Class` et `End Class` instructions :</span><span class="sxs-lookup"><span data-stu-id="f6183-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     <span data-ttu-id="f6183-117">[!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-117">[!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span></span>  
  
     <span data-ttu-id="f6183-118">Déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe.</span><span class="sxs-lookup"><span data-stu-id="f6183-118">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="f6183-119">Vous pouvez rendre champs accessibles en dehors d’une classe à l’aide des modificateurs d’accès comme `Public` qui fournissent un accès plus.</span><span class="sxs-lookup"><span data-stu-id="f6183-119">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="f6183-120">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f6183-120">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="f6183-121">Définir une propriété pour la classe en ajoutant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f6183-121">Define a property for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="f6183-122">[!code-vb[VbVbalrOOP n °&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-122">[!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span></span>  
  
8.  <span data-ttu-id="f6183-123">Définissez une méthode pour la classe en ajoutant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f6183-123">Define a method for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="f6183-124">[!code-vb[VbVbalrOOP&#9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-124">[!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span></span>  
  
9. <span data-ttu-id="f6183-125">Définissez un constructeur paramétré pour la nouvelle classe en ajoutant une procédure nommée `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="f6183-125">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     <span data-ttu-id="f6183-126">[!code-vb[VbVbalrOOP&#10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-126">[!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span></span>  
  
     <span data-ttu-id="f6183-127">Le `Sub New` est appelé automatiquement lorsqu’un objet basé sur cette classe est créé.</span><span class="sxs-lookup"><span data-stu-id="f6183-127">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="f6183-128">Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f6183-128">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="f6183-129">Pour créer un bouton pour tester la classe</span><span class="sxs-lookup"><span data-stu-id="f6183-129">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="f6183-130">Modifiez le formulaire de démarrage en mode design en double-cliquant sur son nom dans **l’Explorateur de solutions** , puis en cliquant sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="f6183-130">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="f6183-131">Par défaut, le formulaire de démarrage pour les projets d’Application Windows est intitulé Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="f6183-131">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="f6183-132">Le formulaire principal s’affiche alors.</span><span class="sxs-lookup"><span data-stu-id="f6183-132">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="f6183-133">Ajoutez un bouton au formulaire principal et double-cliquez dessus pour afficher le code pour le `Button1_Click` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f6183-133">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="f6183-134">Ajoutez le code suivant pour appeler la procédure de test :</span><span class="sxs-lookup"><span data-stu-id="f6183-134">Add the following code to call the test procedure:</span></span>  
  
     <span data-ttu-id="f6183-135">[!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6183-135">[!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span></span>  
  
### <a name="to-run-your-application"></a><span data-ttu-id="f6183-136">Pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="f6183-136">To run your application</span></span>  
  
1.  <span data-ttu-id="f6183-137">Exécutez votre application en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="f6183-137">Run your application by pressing F5.</span></span> <span data-ttu-id="f6183-138">Cliquez sur le bouton du formulaire pour appeler la procédure de test.</span><span class="sxs-lookup"><span data-stu-id="f6183-138">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="f6183-139">Il affiche un message indiquant que l’original `UserName` est « MOORE, BOBBY », parce que la procédure appelée la `Capitalize` méthode de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f6183-139">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="f6183-140">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="f6183-140">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="f6183-141">Le `Button1 Click` procédure modifie la valeur de la `UserName` propriété et affiche un message indiquant que la nouvelle valeur de `UserName` est « Worden, Joe ».</span><span class="sxs-lookup"><span data-stu-id="f6183-141">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6183-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6183-142">See Also</span></span>  
 <span data-ttu-id="f6183-143">[Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span><span class="sxs-lookup"><span data-stu-id="f6183-143">[Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span></span>  
<span data-ttu-id="f6183-144"> [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="f6183-144"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>

