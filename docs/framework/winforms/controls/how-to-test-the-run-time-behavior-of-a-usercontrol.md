---
title: "Comment : tester le comportement d'un UserControl au moment de l'exécution"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48b7c47a14f27439c60280a5c4202e9f4af76397
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="f1440-102">Comment : tester le comportement d'un UserControl au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="f1440-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="f1440-103">Lorsque vous développez un <xref:System.Windows.Forms.UserControl>, vous devez tester son comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f1440-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="f1440-104">Vous pouvez créer un projet d’application Windows distincts et placer votre contrôle sur un formulaire de test, mais cette procédure n’est pas pratique.</span><span class="sxs-lookup"><span data-stu-id="f1440-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="f1440-105">Un moyen plus rapide et plus facile consiste à utiliser le **conteneur de Test UserControl** fournis par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1440-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="f1440-106">Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.</span><span class="sxs-lookup"><span data-stu-id="f1440-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1440-107">Le conteneur de test charger votre <xref:System.Windows.Forms.UserControl>, le contrôle doit avoir au moins un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="f1440-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1440-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="f1440-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f1440-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="f1440-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f1440-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f1440-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1440-111">Un contrôle Visual C++ ne peut pas être testé à l’aide de la **conteneur de Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f1440-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="f1440-112">Pour tester le comportement d’exécution d’un UserControl</span><span class="sxs-lookup"><span data-stu-id="f1440-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="f1440-113">Créer un projet de bibliothèque de contrôles Windows appelé **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="f1440-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="f1440-114">Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="f1440-114">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="f1440-115">Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.Label> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1440-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="f1440-116">Appuyez sur F5 pour générer le projet et exécuter le **conteneur de Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="f1440-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="f1440-117">Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans les **aperçu** volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="f1440-118">Sélectionnez le <xref:System.Windows.Forms.Control.BackColor%2A> propriété affichée dans le <xref:System.Windows.Forms.PropertyGrid> contrôle situé à droite de la **aperçu** volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="f1440-119">Modifiez sa valeur en `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="f1440-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="f1440-120">Observez que le contrôle devient une couleur plus sombre.</span><span class="sxs-lookup"><span data-stu-id="f1440-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="f1440-121">Essayez de modifier d’autres valeurs de propriété et observez l’effet sur votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1440-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="f1440-122">Cliquez sur le **ancrer le contrôle utilisateur remplir** case à cocher ci-dessous le **aperçu** volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="f1440-123">Observez que le contrôle est redimensionné pour remplir le volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="f1440-124">Redimensionner le conteneur de test et observez que le contrôle est redimensionné avec le volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="f1440-125">Fermez le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="f1440-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="f1440-126">Ajoutez un autre contrôle utilisateur à la **TestContainerExample** projet.</span><span class="sxs-lookup"><span data-stu-id="f1440-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="f1440-127">Pour plus d’informations, consultez [NIB : Comment : ajouter des éléments existants à un projet](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="f1440-127">For details, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="f1440-128">Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1440-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="f1440-129">Appuyez sur F5 pour générer le projet et exécuter le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="f1440-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="f1440-130">Cliquez sur le **sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour basculer entre les deux contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1440-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="f1440-131">Contrôles utilisateur à partir d’un autre projet de test</span><span class="sxs-lookup"><span data-stu-id="f1440-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="f1440-132">Vous pouvez tester les contrôles utilisateur à partir d’autres projets dans le conteneur de test de votre projet actuel.</span><span class="sxs-lookup"><span data-stu-id="f1440-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="f1440-133">Pour tester les contrôles utilisateur à partir d’un autre projet</span><span class="sxs-lookup"><span data-stu-id="f1440-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="f1440-134">Créer un projet de bibliothèque de contrôles Windows appelé **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="f1440-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="f1440-135">Pour plus d’informations, consultez [modèle de bibliothèque de contrôles Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="f1440-135">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="f1440-136">Dans le **Concepteur Windows Forms**, faites glisser un <xref:System.Windows.Forms.RadioButton> contrôle depuis la **boîte à outils** sur l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1440-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="f1440-137">Appuyez sur F5 pour générer le projet et exécuter le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="f1440-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="f1440-138">Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans les **aperçu** volet.</span><span class="sxs-lookup"><span data-stu-id="f1440-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="f1440-139">Cliquez sur le **charge** bouton.</span><span class="sxs-lookup"><span data-stu-id="f1440-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="f1440-140">Dans le **ouvrir** boîte de dialogue, accédez à **TestContainerExample**.dll que vous avez créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="f1440-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="f1440-141">Sélectionnez **TestContainerExample**.dll et cliquez sur le **ouvrir** bouton Charger les contrôles utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1440-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="f1440-142">Utilisez le **sélectionner un contrôle utilisateur** <xref:System.Windows.Forms.ComboBox> pour basculer entre les deux contrôles utilisateur à partir de la **TestContainerExample** projet.</span><span class="sxs-lookup"><span data-stu-id="f1440-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1440-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1440-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="f1440-144">Guide pratique pour créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="f1440-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="f1440-145">Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1440-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="f1440-146">Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="f1440-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="f1440-147">Concepteur de contrôles utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1440-147">User Control Designer</span></span>](http://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
