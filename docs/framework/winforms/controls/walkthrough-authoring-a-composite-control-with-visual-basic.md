---
title: "Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c31e76e9f190990f0a3dddab359ef9523783d955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="1ecca-102">Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ecca-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="1ecca-103">Les contrôles composites permettent de créer et de réutiliser des interfaces graphiques personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1ecca-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="1ecca-104">Un contrôle composite est avant tout un composant doté d’une représentation visuelle.</span><span class="sxs-lookup"><span data-stu-id="1ecca-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="1ecca-105">Par conséquent, il peut comporter un ou plusieurs blocs de code, composants ou contrôles Windows Forms qui peuvent en étendre les fonctionnalités en validant les entrées d’utilisateur, en modifiant les propriétés d’affichage ou en effectuant d’autres tâches requises par l’auteur.</span><span class="sxs-lookup"><span data-stu-id="1ecca-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="1ecca-106">Les contrôles composites peuvent être insérés dans les Windows Forms de la même manière que les autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="1ecca-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="1ecca-107">Dans la première partie de cette procédure pas à pas, vous allez créer un contrôle composite simple appelé `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="1ecca-108">Dans la seconde partie de la procédure pas à pas, vous allez étendre les fonctionnalités de `ctlClock` via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="1ecca-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ecca-109">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="1ecca-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1ecca-110">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="1ecca-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1ecca-111">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1ecca-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="1ecca-112">Création du projet</span><span class="sxs-lookup"><span data-stu-id="1ecca-112">Creating the Project</span></span>  
 <span data-ttu-id="1ecca-113">Lorsque vous créez un nouveau projet, vous spécifiez son nom pour définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="1ecca-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="1ecca-114">Pour créer la bibliothèque de contrôles ctlClockLib et le contrôle ctlClock</span><span class="sxs-lookup"><span data-stu-id="1ecca-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="1ecca-115">Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="1ecca-116">Dans la liste des projets [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], sélectionnez le modèle de projet **Bibliothèque de contrôles Windows**, saisissez `ctlClockLib` dans le champ **Nom**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-116">From the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1ecca-117">Le nom du projet, `ctlClockLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ecca-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="1ecca-118">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1ecca-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="1ecca-119">Par exemple, si deux assemblies contiennent des composants nommés `ctlClock`, vous pouvez spécifier votre composant `ctlClock` à l’aide de `ctlClockLib.ctlClock.`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="1ecca-120">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **UserControl1.vb**, puis cliquez sur **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="1ecca-121">Remplacez le nom de fichier par `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="1ecca-122">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».</span><span class="sxs-lookup"><span data-stu-id="1ecca-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ecca-123">Par défaut, un contrôle composite hérite de la <xref:System.Windows.Forms.UserControl> classe fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="1ecca-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="1ecca-124">La <xref:System.Windows.Forms.UserControl> classe fournit les fonctionnalités requises par les contrôles composites et implémente des méthodes et propriétés standard.</span><span class="sxs-lookup"><span data-stu-id="1ecca-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="1ecca-125">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1ecca-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="1ecca-126">Ajout de composants et de contrôles Windows au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="1ecca-127">L’interface visuelle est un composant essentiel de votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="1ecca-128">Cette interface visuelle est implémentée par l’ajout d’un ou de plusieurs contrôles Windows sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="1ecca-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="1ecca-129">Dans la démonstration suivante, vous allez intégrer des contrôles Windows à votre contrôle composite et écrire du code pour implémenter des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="1ecca-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="1ecca-130">Pour ajouter une étiquette et une minuterie à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="1ecca-131">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="1ecca-132">Dans la boîte à outils, développez le nœud **Contrôles communs**, puis double-cliquez sur **Étiquette**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="1ecca-133">A <xref:System.Windows.Forms.Label> contrôle nommé `Label1` est ajouté à votre contrôle sur l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="1ecca-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="1ecca-134">Dans le concepteur, cliquez sur **Label1**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="1ecca-135">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="1ecca-136">Propriété</span><span class="sxs-lookup"><span data-stu-id="1ecca-136">Property</span></span>|<span data-ttu-id="1ecca-137">Remplacer par</span><span class="sxs-lookup"><span data-stu-id="1ecca-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="1ecca-138">**Name**</span><span class="sxs-lookup"><span data-stu-id="1ecca-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="1ecca-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="1ecca-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="1ecca-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="1ecca-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="1ecca-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="1ecca-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="1ecca-142">Dans la **boîte à outils**, développez le nœud **Composants**, puis double-cliquez sur **Minuterie**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="1ecca-143">Car un <xref:System.Windows.Forms.Timer> est un composant, il n’a aucune représentation visuelle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ecca-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="1ecca-144">Par conséquent, il n’apparaît pas avec les contrôles sur l’aire du concepteur, mais plutôt dans le Concepteur de composants (une barre d’état située en bas de l’aire du concepteur).</span><span class="sxs-lookup"><span data-stu-id="1ecca-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="1ecca-145">Dans le Concepteur de composants, cliquez sur **Timer1**, puis définissez le <xref:System.Windows.Forms.Timer.Interval%2A> propriété `1000` et <xref:System.Windows.Forms.Timer.Enabled%2A> propriété `True`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="1ecca-146">Le <xref:System.Windows.Forms.Timer.Interval%2A> propriété contrôle la fréquence des graduations du composant timer.</span><span class="sxs-lookup"><span data-stu-id="1ecca-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="1ecca-147">À chaque nouvelle graduation du composant `Timer1`, le code est exécuté dans l’événement `Timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="1ecca-148">L’intervalle représente le nombre de millisecondes entre les graduations.</span><span class="sxs-lookup"><span data-stu-id="1ecca-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="1ecca-149">Dans le Concepteur de composants, double-cliquez sur **Timer1** pour accéder à l’événement `Timer1_Tick` pour `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="1ecca-150">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="1ecca-151">Remplacez le paramètre de modificateur d’accès `Private` par `Protected`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="1ecca-152">Ce code entraînera l’affichage de l’heure actuelle dans `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="1ecca-153">Étant donné que l’intervalle du composant `Timer1` a été défini sur `1000`, cet événement se produira toutes les mille millisecondes, mettant ainsi l’heure à jour toutes les secondes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="1ecca-154">Modifiez la méthode afin qu’elle soit remplaçable.</span><span class="sxs-lookup"><span data-stu-id="1ecca-154">Modify the method to be overridable.</span></span> <span data-ttu-id="1ecca-155">Pour plus d’informations, consultez la section « Héritage d’un contrôle utilisateur » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1ecca-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="1ecca-156">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1ecca-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="1ecca-157">Ajout de propriétés au contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="1ecca-158">Le contrôle horloge intègre à présent un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.Timer> composant, chacun avec son propre jeu de propriétés inhérentes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="1ecca-159">Même si les propriétés individuelles de ces contrôles ne seront pas accessibles aux autres utilisateurs de votre contrôle, vous pouvez créer et exposer des propriétés personnalisées en écrivant les blocs de code appropriés.</span><span class="sxs-lookup"><span data-stu-id="1ecca-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="1ecca-160">Dans la procédure suivante, vous allez ajouter des propriétés à votre contrôle qui permettent à l’utilisateur de modifier la couleur de l’arrière-plan et du texte.</span><span class="sxs-lookup"><span data-stu-id="1ecca-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="1ecca-161">Pour ajouter une propriété à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="1ecca-162">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClock.vb**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="1ecca-163">L’éditeur de code de votre contrôle s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="1ecca-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="1ecca-164">Recherchez l’instruction `Public Class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="1ecca-165">Sous l’instruction, saisissez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="1ecca-166">Ces instructions créent les variables privées que vous utiliserez pour stocker les valeurs des propriétés que vous allez créer.</span><span class="sxs-lookup"><span data-stu-id="1ecca-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="1ecca-167">Insérez le code suivant sous les déclarations de variable de l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="1ecca-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="1ecca-168">Le code précédent crée deux propriétés personnalisées, `ClockForeColor` et `ClockBackColor`, auxquelles les autres utilisateurs du contrôle pourront accéder en appelant l’instruction `Property`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="1ecca-169">`Get` et `Set` fournissent des instructions pour le stockage et la récupération de la valeur de propriété, ainsi que le code pour intégrer les fonctionnalités appropriées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="1ecca-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="1ecca-170">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1ecca-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="1ecca-171">Test du contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecca-171">Testing the Control</span></span>  
 <span data-ttu-id="1ecca-172">Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1ecca-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="1ecca-173">Testez le comportement de votre contrôle au moment de l’exécution et testez ses propriétés avec le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="1ecca-174">Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="1ecca-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="1ecca-175">Pour tester votre contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecca-175">To test your control</span></span>  
  
1.  <span data-ttu-id="1ecca-176">Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="1ecca-177">Dans la grille des propriétés du conteneur de test, sélectionnez la propriété `ClockBackColor`, puis cliquez sur la flèche déroulante pour afficher la palette de couleurs.</span><span class="sxs-lookup"><span data-stu-id="1ecca-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="1ecca-178">Choisissez une couleur en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="1ecca-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="1ecca-179">La couleur sélectionnée devient la couleur d’arrière-plan de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="1ecca-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="1ecca-180">Utilisez une séquence d’événements similaire pour vérifier que la propriété `ClockForeColor` fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="1ecca-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="1ecca-181">Cliquez sur **Fermer** pour fermer le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="1ecca-182">Dans cette section et les sections précédentes, vous avez vu comment les composants et contrôles Windows peuvent être combinés avec du code et de l’empaquetage afin d’offrir des fonctionnalités personnalisées sous la forme d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="1ecca-183">Vous avez appris à exposer des propriétés dans votre contrôle composite et à tester votre contrôle après sa configuration.</span><span class="sxs-lookup"><span data-stu-id="1ecca-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="1ecca-184">Dans la section suivante, vous allez apprendre à créer un contrôle composite hérité en utilisant `ctlClock` comme base.</span><span class="sxs-lookup"><span data-stu-id="1ecca-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="1ecca-185">Héritage d’un contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="1ecca-186">Dans les sections précédentes, vous avez appris à combiner du code, des composants et des contrôles Windows pour créer des contrôles composites réutilisables.</span><span class="sxs-lookup"><span data-stu-id="1ecca-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="1ecca-187">Votre contrôle composite peut maintenant être utilisé comme base pour créer d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="1ecca-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="1ecca-188">Le processus qui consiste à créer une classe à partir d’une classe de base est appelé *héritage*.</span><span class="sxs-lookup"><span data-stu-id="1ecca-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="1ecca-189">Dans cette section, vous allez créer un contrôle composite nommé `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="1ecca-190">Ce contrôle sera créé à partir de son contrôle parent, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="1ecca-191">Vous allez apprendre à étendre les fonctionnalités de `ctlClock` en remplaçant les méthodes parentes et en ajoutant de nouvelles méthodes et propriétés.</span><span class="sxs-lookup"><span data-stu-id="1ecca-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="1ecca-192">La première étape de la création d’un contrôle hérité consiste à le dériver de son parent.</span><span class="sxs-lookup"><span data-stu-id="1ecca-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="1ecca-193">Cette action crée un contrôle qui possède toutes les propriétés, méthodes et caractéristiques graphiques du contrôle parent, mais qui peut également être utilisé comme base pour l’ajout de fonctionnalités nouvelles ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="1ecca-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="1ecca-194">Pour créer le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="1ecca-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="1ecca-195">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, pointez sur **Ajouter**, puis cliquez sur **Contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="1ecca-196">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="1ecca-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1ecca-197">Sélectionnez le modèle **Contrôle utilisateur hérité**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="1ecca-198">Dans le champ **Nom**, saisissez `ctlAlarmClock.vb`, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="1ecca-199">La boîte de dialogue **Sélecteur d’héritage** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1ecca-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="1ecca-200">Sous **Nom du composant**, double-cliquez sur **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="1ecca-201">Dans l’Explorateur de solutions, parcourez les projets en cours.</span><span class="sxs-lookup"><span data-stu-id="1ecca-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ecca-202">Un fichier appelé **ctlAlarmClock.vb** a été ajouté au projet actuel.</span><span class="sxs-lookup"><span data-stu-id="1ecca-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="1ecca-203">Ajout de propriétés d’alarme</span><span class="sxs-lookup"><span data-stu-id="1ecca-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="1ecca-204">Les propriétés sont ajoutées à un contrôle hérité de la même façon qu’elles sont ajoutées à un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="1ecca-205">Vous allez maintenant utiliser la syntaxe de déclaration de propriété pour ajouter deux propriétés à votre contrôle : `AlarmTime`, qui stocke la date et l’heure de désactivation de l’alarme, et `AlarmSet`, qui indique si oui ou non l’alarme est définie.</span><span class="sxs-lookup"><span data-stu-id="1ecca-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="1ecca-206">Pour ajouter des propriétés à votre contrôle composite</span><span class="sxs-lookup"><span data-stu-id="1ecca-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="1ecca-207">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="1ecca-208">Recherchez la déclaration de classe pour le contrôle ctlAlarmClock qui apparaît sous la forme `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="1ecca-209">Dans la déclaration de classe, insérez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="1ecca-210">Ajout de l’interface graphique du contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecca-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="1ecca-211">Votre contrôle hérité possède une interface visuelle qui est identique à celle du contrôle dont il a hérité.</span><span class="sxs-lookup"><span data-stu-id="1ecca-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="1ecca-212">Il possède les mêmes contrôles constitutifs que son contrôle parent, mais les propriétés de ces contrôles ne seront pas disponibles, sauf si elles ont été spécifiquement exposées.</span><span class="sxs-lookup"><span data-stu-id="1ecca-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="1ecca-213">Vous pouvez ajouter des éléments à l’interface graphique d’un contrôle composite hérité de la même manière que vous ajoutez des éléments à tout autre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="1ecca-214">Pour continuer à ajouter des éléments à l’interface visuelle de votre alarme, vous allez ajouter un contrôle Étiquette qui clignote lorsque l’alarme sonne.</span><span class="sxs-lookup"><span data-stu-id="1ecca-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="1ecca-215">Pour ajouter le contrôle Étiquette</span><span class="sxs-lookup"><span data-stu-id="1ecca-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="1ecca-216">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="1ecca-217">Le concepteur pour `ctlAlarmClock` s’ouvre dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="1ecca-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="1ecca-218">Cliquez sur `lblDisplay` (la partie visible du contrôle) et affichez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="1ecca-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ecca-219">Toutes les propriétés qui s’affichent sont grisées.</span><span class="sxs-lookup"><span data-stu-id="1ecca-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="1ecca-220">Cela indique que ces propriétés sont propres à `lblDisplay` et ne peuvent pas être modifiées ou sélectionnées dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="1ecca-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="1ecca-221">Par défaut, les contrôles contenus dans un contrôle composite sont à l’état `Private`, et leurs propriétés ne sont accessibles d’aucune façon.</span><span class="sxs-lookup"><span data-stu-id="1ecca-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ecca-222">Si vous souhaitez que d’autres utilisateurs de votre contrôle composite puissent accéder à ses contrôles internes, définissez leur état sur `Public` ou `Protected`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="1ecca-223">Cela vous permettra de définir et de modifier les propriétés des contrôles contenus dans votre contrôle composite à l’aide du code approprié.</span><span class="sxs-lookup"><span data-stu-id="1ecca-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="1ecca-224">Ajouter un <xref:System.Windows.Forms.Label> vers votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="1ecca-225">À l’aide de la souris, faites glisser le <xref:System.Windows.Forms.Label> contrôle immédiatement sous la zone d’affichage.</span><span class="sxs-lookup"><span data-stu-id="1ecca-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="1ecca-226">Dans la fenêtre Propriétés, définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="1ecca-227">Propriété</span><span class="sxs-lookup"><span data-stu-id="1ecca-227">Property</span></span>|<span data-ttu-id="1ecca-228">Paramètre</span><span class="sxs-lookup"><span data-stu-id="1ecca-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="1ecca-229">**Name**</span><span class="sxs-lookup"><span data-stu-id="1ecca-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="1ecca-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="1ecca-230">**Text**</span></span>|<span data-ttu-id="1ecca-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="1ecca-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="1ecca-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="1ecca-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="1ecca-233">**Visible**</span><span class="sxs-lookup"><span data-stu-id="1ecca-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="1ecca-234">Ajout de la fonctionnalité d’alarme</span><span class="sxs-lookup"><span data-stu-id="1ecca-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="1ecca-235">Dans les procédures précédentes, vous avez ajouté des propriétés et un contrôle permettant d’activer la fonctionnalité d’alarme dans votre contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="1ecca-236">Dans cette procédure, vous allez ajouter du code pour comparer l’heure actuelle à l’heure de l’alarme et, si elles sont identiques, déclencher le son et le clignotement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="1ecca-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="1ecca-237">En remplaçant la méthode `Timer1_Tick` de `ctlClock` et en lui ajoutant du code, vous allez étendre les capacités de `ctlAlarmClock` tout en conservant les fonctionnalités inhérentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="1ecca-238">Pour remplacer la méthode Timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="1ecca-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="1ecca-239">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="1ecca-240">Recherchez l’instruction `Private blnAlarmSet As Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="1ecca-241">Juste en dessous de l’instruction, ajoutez l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="1ecca-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="1ecca-242">Recherchez l’instruction `End Class` au bas de la page.</span><span class="sxs-lookup"><span data-stu-id="1ecca-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="1ecca-243">Juste avant l’instruction `End Class`, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="1ecca-244">L’ajout de ce code permet d’effectuer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="1ecca-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="1ecca-245">L’instruction `Overrides` ordonne au contrôle d’utiliser cette méthode à la place de la méthode héritée du contrôle de base.</span><span class="sxs-lookup"><span data-stu-id="1ecca-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="1ecca-246">Lorsque cette méthode est appelée, elle appelle la méthode qu’elle remplace en appelant l’instruction `MyBase.Timer1_Tick`, ce qui permet de s’assurer que toutes les fonctionnalités intégrées au contrôle d’origine sont également intégrées à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="1ecca-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="1ecca-247">Du code supplémentaire est ensuite exécuté pour intégrer la fonctionnalité d’alarme.</span><span class="sxs-lookup"><span data-stu-id="1ecca-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="1ecca-248">Lorsque l’alarme se déclenche, un contrôle Étiquette clignotant apparaît et un signal sonore retentit.</span><span class="sxs-lookup"><span data-stu-id="1ecca-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ecca-249">Comme vous remplacez un gestionnaire d’événements hérité, il n’est pas nécessaire de spécifier l’événement avec le mot clé `Handles`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="1ecca-250">L’événement est déjà rattaché.</span><span class="sxs-lookup"><span data-stu-id="1ecca-250">The event is already hooked up.</span></span> <span data-ttu-id="1ecca-251">Tout ce que vous remplacez est l’implémentation du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="1ecca-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="1ecca-252">Votre contrôle d’alarme est presque terminé.</span><span class="sxs-lookup"><span data-stu-id="1ecca-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="1ecca-253">La seule chose qui reste à faire est de mettre en place un moyen de le désactiver.</span><span class="sxs-lookup"><span data-stu-id="1ecca-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="1ecca-254">Pour ce faire, vous allez ajouter du code à la méthode `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="1ecca-255">Pour implémenter la méthode de désactivation</span><span class="sxs-lookup"><span data-stu-id="1ecca-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="1ecca-256">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlAlarmClock.vb**, puis cliquez sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="1ecca-257">Dans le concepteur, double-cliquez sur **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="1ecca-258">**L’éditeur de code** s’ouvre à la ligne `Private Sub lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="1ecca-259">Modifiez cette méthode afin qu’elle ressemble au code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="1ecca-260">Dans le menu **Fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1ecca-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="1ecca-261">Utilisation du contrôle hérité sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="1ecca-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="1ecca-262">Vous pouvez tester votre contrôle hérité de la même façon que vous avez testé le contrôle de la classe de base, `ctlClock` : appuyez sur F5 pour générer le projet et exécutez votre contrôle dans le **Conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="1ecca-263">Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="1ecca-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="1ecca-264">Pour pouvoir utiliser votre contrôle, vous devrez l’héberger dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="1ecca-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="1ecca-265">À l’instar d’un contrôle composite standard, un contrôle composite hérité ne peut pas fonctionner de manière autonome et doit être hébergé dans un formulaire ou un autre conteneur.</span><span class="sxs-lookup"><span data-stu-id="1ecca-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="1ecca-266">Étant donné que `ctlAlarmClock` présente davantage de fonctionnalités, du code supplémentaire est nécessaire pour le tester.</span><span class="sxs-lookup"><span data-stu-id="1ecca-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="1ecca-267">Dans cette procédure, vous allez écrire un programme simple afin de tester les fonctionnalités de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="1ecca-268">Vous allez écrire du code pour définir et afficher la propriété `AlarmTime` de `ctlAlarmClock`, puis vous testerez ses fonctions inhérentes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="1ecca-269">Pour générer votre contrôle et l’ajouter à un formulaire de test</span><span class="sxs-lookup"><span data-stu-id="1ecca-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="1ecca-270">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **ctlClockLib**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="1ecca-271">Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="1ecca-272">Ajoutez un nouveau projet **d’application Windows** à la solution et nommez-le `Test`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="1ecca-273">Le projet **Test** est ajouté à l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="1ecca-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="1ecca-274">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet `Test`, puis cliquez sur **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="1ecca-275">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="1ecca-276">Le projet **ctlClockLib** s’affiche sous **Nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="1ecca-277">Double-cliquez sur **ctlClockLib** pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="1ecca-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="1ecca-278">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="1ecca-279">Dans la **boîte à outils**, développez le nœud **Composants ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="1ecca-280">Double-cliquez sur **ctlAlarmClock** pour ajouter une instance de `ctlAlarmClock` à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="1ecca-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="1ecca-281">Dans le **boîte à outils**, recherchez et double-cliquez sur **DateTimePicker** pour ajouter un <xref:System.Windows.Forms.DateTimePicker> le contrôle à votre formulaire, puis ajoutez un <xref:System.Windows.Forms.Label> contrôle en double-cliquant sur **étiquette**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="1ecca-282">Utilisez la souris pour positionner les contrôles à un endroit approprié sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1ecca-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="1ecca-283">Définissez les propriétés de ces contrôles de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="1ecca-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="1ecca-284">Contrôle</span><span class="sxs-lookup"><span data-stu-id="1ecca-284">Control</span></span>|<span data-ttu-id="1ecca-285">Propriété</span><span class="sxs-lookup"><span data-stu-id="1ecca-285">Property</span></span>|<span data-ttu-id="1ecca-286">Value</span><span class="sxs-lookup"><span data-stu-id="1ecca-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="1ecca-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="1ecca-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="1ecca-288">**Name**</span><span class="sxs-lookup"><span data-stu-id="1ecca-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="1ecca-289">**Name**</span><span class="sxs-lookup"><span data-stu-id="1ecca-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="1ecca-290">**Format**</span><span class="sxs-lookup"><span data-stu-id="1ecca-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="1ecca-291">Dans le concepteur, double-cliquez sur **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="1ecca-292">**L’éditeur de code** s’ouvre à la ligne `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="1ecca-293">Modifiez le code afin qu’il ressemble à l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1ecca-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="1ecca-294">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Test**, puis cliquez sur **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="1ecca-295">Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="1ecca-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="1ecca-296">Le programme de test démarre.</span><span class="sxs-lookup"><span data-stu-id="1ecca-296">The test program starts.</span></span> <span data-ttu-id="1ecca-297">Notez que l’heure actuelle est mise à jour dans le `ctlAlarmClock` contrôle et que l’heure de début est affichée dans le <xref:System.Windows.Forms.DateTimePicker> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1ecca-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="1ecca-298">Cliquez sur le <xref:System.Windows.Forms.DateTimePicker> où sont affichées les minutes de l’heure.</span><span class="sxs-lookup"><span data-stu-id="1ecca-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="1ecca-299">À l’aide du clavier, définissez une valeur pour les minutes comportant une minute de plus que l’heure actuelle affichée par `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="1ecca-300">L’heure de déclenchement de l’alarme apparaît dans `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="1ecca-301">Attendez que l’heure affichée atteigne l’heure de déclenchement de l’alarme.</span><span class="sxs-lookup"><span data-stu-id="1ecca-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="1ecca-302">Lorsque l’heure affichée atteint l’heure sur laquelle l’alarme a été définie, un signal sonore retentit et `lblAlarm` se met à clignoter.</span><span class="sxs-lookup"><span data-stu-id="1ecca-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="1ecca-303">Désactivez l’alarme en cliquant sur `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="1ecca-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="1ecca-304">Vous pouvez maintenant réinitialiser l’alarme.</span><span class="sxs-lookup"><span data-stu-id="1ecca-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="1ecca-305">Cette procédure pas à pas a abordé plusieurs concepts clés.</span><span class="sxs-lookup"><span data-stu-id="1ecca-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="1ecca-306">Vous avez appris à créer un contrôle composite en combinant des contrôles et des composants dans un conteneur de contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="1ecca-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="1ecca-307">Vous avez appris à ajouter des propriétés à votre contrôle et à écrire du code pour implémenter des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1ecca-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="1ecca-308">Dans la dernière section, vous avez appris à étendre les fonctionnalités d’un contrôle composite grâce à l’héritage et à modifier les fonctionnalités des méthodes hôtes en remplaçant ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="1ecca-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ecca-309">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ecca-309">See Also</span></span>  
 [<span data-ttu-id="1ecca-310">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="1ecca-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="1ecca-311">Guide pratique pour créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="1ecca-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="1ecca-312">Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="1ecca-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="1ecca-313">Procédures pas à pas de la création de composants</span><span class="sxs-lookup"><span data-stu-id="1ecca-313">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
