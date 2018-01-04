---
title: "Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e413a7ddf7e256538e56876712a54f875392b59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="d3e8c-102">Procédure pas à pas : activation de la fonction glisser-déplacer sur un contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3e8c-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="d3e8c-103">Cette procédure pas à pas montre comment créer un contrôle utilisateur personnalisé qui peut participer à un transfert de données par glisser-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3e8c-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="d3e8c-104">Dans cette procédure pas à pas, vous allez créer un WPF personnalisé <xref:System.Windows.Controls.UserControl> qui représente une forme de cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="d3e8c-105">Vous implémentez la fonctionnalité sur le contrôle pour activer le transfert de données par glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="d3e8c-106">Par exemple, si vous faites glisser un contrôle de cercle sur un autre, les données de couleur de remplissage sont copiées du cercle source vers la cible.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="d3e8c-107">Si vous faites glisser un contrôle Circle à un <xref:System.Windows.Controls.TextBox>, la représentation sous forme de chaîne de la couleur de remplissage est copiée vers le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d3e8c-108">Vous créerez également une petite application qui contient deux contrôles de panneau de configuration et un <xref:System.Windows.Controls.TextBox> pour tester la fonctionnalité de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="d3e8c-109">Vous écrivez du code qui permet aux panneaux de traiter les données de cercle déplacées, ce qui vous permet de déplacer ou copier des cercles de la collection d’enfants d’un panneau à l’autre.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="d3e8c-110">Cette procédure pas à pas décrit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="d3e8c-111">Créer un contrôle utilisateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="d3e8c-112">Permettre au contrôle utilisateur d’être une source de glissement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="d3e8c-113">Permettre au contrôle utilisateur d’être une cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="d3e8c-114">Permettre à un panneau de recevoir des données déplacées à partir du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d3e8c-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d3e8c-115">Prerequisites</span></span>  
 <span data-ttu-id="d3e8c-116">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="d3e8c-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="d3e8c-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="d3e8c-118">Création du projet d’application</span><span class="sxs-lookup"><span data-stu-id="d3e8c-118">Creating the Application Project</span></span>  
 <span data-ttu-id="d3e8c-119">Dans cette section, vous allez créer l’infrastructure d’application, qui comprend une page principale avec deux panneaux et un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="d3e8c-120">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="d3e8c-120">To create the project</span></span>  
  
1.  <span data-ttu-id="d3e8c-121">Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="d3e8c-122">Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="d3e8c-122">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="d3e8c-123">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="d3e8c-124">Ajoutez le balisage suivant entre les balises <xref:System.Windows.Controls.Grid> balises.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="d3e8c-125">Ce balisage crée l’interface utilisateur pour l’application de test.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="d3e8c-126">Ajout d'un nouveau contrôle utilisateur au projet</span><span class="sxs-lookup"><span data-stu-id="d3e8c-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="d3e8c-127">Dans cette section, vous ajoutez un nouveau contrôle utilisateur au projet.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="d3e8c-128">Pour ajouter un nouveau contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3e8c-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="d3e8c-129">Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="d3e8c-130">Dans la boîte de dialogue Ajouter un nouvel élément, remplacez le nom par `Circle.xaml`, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="d3e8c-131">Circle.XAML et son code-behind sont ajoutés au projet.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="d3e8c-132">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="d3e8c-133">Ce fichier doit contenir les éléments d’interface utilisateur du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="d3e8c-134">Ajoutez le balisage suivant à la racine <xref:System.Windows.Controls.Grid> pour créer un contrôle utilisateur simple qui présente un cercle bleu comme interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="d3e8c-135">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="d3e8c-136">En C#, ajoutez le code suivant après le constructeur par défaut pour créer un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="d3e8c-137">En Visual Basic, ajoutez le code suivant pour créer un constructeur par défaut et un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="d3e8c-138">Pour que le contrôle utilisateur puisse être copié, vous ajoutez une méthode de constructeur de copie dans le fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="d3e8c-139">Dans le contrôle utilisateur de cercle simplifié, vous copiez uniquement les valeurs de remplissage et de taille du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="d3e8c-140">Pour ajouter le contrôle utilisateur à la fenêtre principale</span><span class="sxs-lookup"><span data-stu-id="d3e8c-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="d3e8c-141">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="d3e8c-142">Ajoutez le code XAML suivant à l’ouverture <xref:System.Windows.Window> balise pour créer une référence d’espace de noms XML à l’application actuelle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="d3e8c-143">Dans la première <xref:System.Windows.Controls.StackPanel>, ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur cercle dans le premier panneau.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="d3e8c-144">Le code XAML complet pour le panneau ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="d3e8c-145">Implémentation d’événements de source de glissement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3e8c-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="d3e8c-146">Dans cette section, vous remplace le <xref:System.Windows.UIElement.OnMouseMove%2A> (méthode) et lancer l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="d3e8c-147">Si une opération de glissement n’est démarrée (un bouton de la souris est enfoncé et la souris est déplacée), vous créez un package les données à transférer dans un <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d3e8c-148">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="d3e8c-149">Pour lancer une opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="d3e8c-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="d3e8c-150">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="d3e8c-151">Ajoutez le code suivant <xref:System.Windows.UIElement.OnMouseMove%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.MouseMove> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="d3e8c-152">Cela <xref:System.Windows.UIElement.OnMouseMove%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-153">Vérifie si le bouton gauche de la souris est enfoncé quand la souris se déplace.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="d3e8c-154">Regroupe les données Circle dans un <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="d3e8c-155">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="d3e8c-156">Appelle la méthode statique <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> méthode pour lancer l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="d3e8c-157">Vous passez les trois paramètres suivants pour le <xref:System.Windows.DragDrop.DoDragDrop%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="d3e8c-158">`dragSource` : Référence à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="d3e8c-159">`data`– Les <xref:System.Windows.DataObject> créé dans le code précédent.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="d3e8c-160">`allowedEffects`– Les opérations de glisser-déplacer autorisées qui sont <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="d3e8c-161">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="d3e8c-162">Cliquez sur un des contrôles Circle et faites-le glisser sur les panneaux, cercle et le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d3e8c-163">Lorsque vous faites glisser sur le <xref:System.Windows.Controls.TextBox>, le curseur se transforme pour indiquer un déplacement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="d3e8c-164">Tout en faisant glisser un cercle sur le <xref:System.Windows.Controls.TextBox>, appuyez sur la touche CTRL ENFONCÉE.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="d3e8c-165">Notez que le curseur change pour indiquer une copie.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="d3e8c-166">Faites glisser et déposez un cercle sur le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d3e8c-167">La représentation sous forme de chaîne de couleur de remplissage du cercle est ajoutée à la <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="d3e8c-168">![Représentation sous forme de chaîne de la couleur de remplissage du cercle](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="d3e8c-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="d3e8c-169">Par défaut, le curseur change pendant une opération de glisser-déplacer pour indiquer l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="d3e8c-170">Vous pouvez personnaliser les commentaires donnés à l’utilisateur en gérant le <xref:System.Windows.UIElement.GiveFeedback> événement et en définissant un autre curseur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="d3e8c-171">Pour transmettre des commentaires à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3e8c-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="d3e8c-172">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="d3e8c-173">Ajoutez le code suivant <xref:System.Windows.UIElement.OnGiveFeedback%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.GiveFeedback> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="d3e8c-174">Cela <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-175">Vérifie la <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeurs qui sont définies dans la cible de dépôt <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="d3e8c-176">Définit un curseur personnalisé basé sur le <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="d3e8c-177">Le curseur a pour objectif de fournir des commentaires visuels à l’utilisateur sur l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="d3e8c-178">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="d3e8c-179">Faites glisser un de cercle contrôle sur les panneaux, cercle, et le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="d3e8c-180">Notez que les curseurs sont à présent les curseurs personnalisés que vous avez spécifié dans le <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="d3e8c-181">![Glisser-déplacer avec des curseurs personnalisés](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="d3e8c-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="d3e8c-182">Sélectionnez le texte `green` à partir de la <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="d3e8c-183">Faites glisser le texte `green` sur un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="d3e8c-184">Notez que les curseurs par défaut sont affichés pour indiquer les effets de l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="d3e8c-185">Le curseur de commentaire est toujours défini par la source de glissement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="d3e8c-186">Implémentation d’événements de cible de déplacement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="d3e8c-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="d3e8c-187">Dans cette section, vous indiquez que le contrôle utilisateur est une cible de déplacement, vous substituez les méthodes qui permettent au contrôle utilisateur d’être une cible de déplacement et vous traitez les données qui sont déplacées sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="d3e8c-188">Pour permettre au contrôle utilisateur d’être une cible de déplacement</span><span class="sxs-lookup"><span data-stu-id="d3e8c-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="d3e8c-189">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="d3e8c-190">Dans l’ouverture <xref:System.Windows.Controls.UserControl> , ajoutez le <xref:System.Windows.UIElement.AllowDrop%2A> propriété et affectez-lui la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="d3e8c-191">Le <xref:System.Windows.UIElement.OnDrop%2A> méthode est appelée lorsque le <xref:System.Windows.UIElement.AllowDrop%2A> est définie sur `true` et données à partir de la source de glissement sont supprimées sur le contrôle utilisateur Circle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="d3e8c-192">Dans cette méthode, vous traitez les données qui ont été déplacées et appliquez les données au cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="d3e8c-193">Pour traiter les données déplacées</span><span class="sxs-lookup"><span data-stu-id="d3e8c-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="d3e8c-194">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="d3e8c-195">Ajoutez le code suivant <xref:System.Windows.UIElement.OnDrop%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.Drop> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="d3e8c-196">Cela <xref:System.Windows.UIElement.OnDrop%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-197">Utilise le <xref:System.Windows.DataObject.GetDataPresent%2A> méthode permettant de vérifier si les données glissées contiennent un objet string.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="d3e8c-198">Utilise le <xref:System.Windows.DataObject.GetData%2A> méthode pour extraire les données de chaîne si elle est présente.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="d3e8c-199">Utilise un <xref:System.Windows.Media.BrushConverter> tente de convertir la chaîne en un <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="d3e8c-200">Si la conversion réussit, applique le pinceau pour le <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle Circle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="d3e8c-201">Marque le <xref:System.Windows.UIElement.Drop> événement comme géré.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="d3e8c-202">Vous devez marquer l’événement de déplacement comme étant géré pour que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur de cercle l’a géré.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="d3e8c-203">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="d3e8c-204">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="d3e8c-205">Faites glisser le texte vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="d3e8c-206">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="d3e8c-207">![Convertir une chaîne en pinceau](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="d3e8c-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="d3e8c-208">Tapez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="d3e8c-209">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="d3e8c-210">Faites le glisser vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="d3e8c-211">Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du cercle ne change pas, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="d3e8c-212">Faites glisser le contrôle de cercle vert et déplacez-le sur le contrôle de cercle bleu.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="d3e8c-213">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="d3e8c-214">Notez que le curseur est affiché varie selon que le <xref:System.Windows.Controls.TextBox> ou le cercle vide est la source de glissement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="d3e8c-215">Définition de la <xref:System.Windows.UIElement.AllowDrop%2A> propriété `true` et traiter les données déplacées est tout ce qui est nécessaire pour activer un élément à une cible de dépôt.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="d3e8c-216">Toutefois, pour fournir une meilleure expérience utilisateur, vous devez également gérer les <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, et <xref:System.Windows.UIElement.DragOver> événements.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="d3e8c-217">Dans ces événements, vous pouvez effectuer des vérifications et fournir des commentaires supplémentaires à l’utilisateur avant de déplacer les données.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="d3e8c-218">Quand les données sont glissées sur le contrôle utilisateur de cercle, le contrôle doit notifier la source de glissement si elle peut ou non traiter les données en cours de glissement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="d3e8c-219">Si le contrôle ne sait pas comment traiter les données, il doit refuser le déplacement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="d3e8c-220">Pour ce faire, vous allez gérer les <xref:System.Windows.UIElement.DragOver> événement et définissez le <xref:System.Windows.DragEventArgs.Effects%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="d3e8c-221">Pour vérifier que le déplacement de données est autorisé</span><span class="sxs-lookup"><span data-stu-id="d3e8c-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="d3e8c-222">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="d3e8c-223">Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragOver%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragOver> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="d3e8c-224">Cela <xref:System.Windows.UIElement.OnDragOver%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-225">Affecte la valeur <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="d3e8c-226">Exécute les mêmes vérifications sont effectuées dans le <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="d3e8c-227">Si le contrôle utilisateur peut traiter les données, définit les <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="d3e8c-228">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="d3e8c-229">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="d3e8c-230">Faites glisser le texte vers un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="d3e8c-231">Notez que le curseur change à présent pour indiquer que le déplacement n’est pas autorisé, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="d3e8c-232">Vous pouvez améliorer l’expérience utilisateur en appliquant un aperçu de l’opération de déplacement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="d3e8c-233">Pour le contrôle utilisateur Circle, remplace le <xref:System.Windows.UIElement.OnDragEnter%2A> et <xref:System.Windows.UIElement.OnDragLeave%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="d3e8c-234">Lorsqu’il sont déplacées les données sur le contrôle, l’arrière-plan actuel <xref:System.Windows.Shapes.Shape.Fill%2A> est enregistré dans une variable d’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="d3e8c-235">La chaîne est ensuite convertie en un pinceau et appliquée à la <xref:System.Windows.Shapes.Ellipse> qui fournit du cercle l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="d3e8c-236">Si les données sont déplacées hors du cercle sans en cours de suppression d’origine <xref:System.Windows.Shapes.Shape.Fill%2A> valeur est de nouveau appliquée au cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="d3e8c-237">Pour afficher un aperçu du résultat de l’opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="d3e8c-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="d3e8c-238">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="d3e8c-239">Dans la classe Circle, déclarez un private <xref:System.Windows.Media.Brush> variable nommée `_previousFill` et initialisez-le à `null`.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="d3e8c-240">Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragEnter%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragEnter> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="d3e8c-241">Cela <xref:System.Windows.UIElement.OnDragEnter%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-242">Enregistre le <xref:System.Windows.Shapes.Shape.Fill%2A> propriété de la <xref:System.Windows.Shapes.Ellipse> dans le `_previousFill` variable.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="d3e8c-243">Exécute les mêmes vérifications sont effectuées dans le <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si les données peuvent être converties en un <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="d3e8c-244">Si les données sont converties à valide <xref:System.Windows.Media.Brush>, s’applique à la <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="d3e8c-245">Ajoutez le code suivant <xref:System.Windows.UIElement.OnDragLeave%2A> override pour fournir la gestion de classe pour le <xref:System.Windows.UIElement.DragLeave> événement.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="d3e8c-246">Cela <xref:System.Windows.UIElement.OnDragLeave%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-247">S’applique le <xref:System.Windows.Media.Brush> enregistrées dans le `_previousFill` variable à la <xref:System.Windows.Shapes.Shape.Fill%2A> de la <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle utilisateur Circle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="d3e8c-248">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="d3e8c-249">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="d3e8c-250">Faites glisser le texte sur un contrôle de cercle sans le déplacer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="d3e8c-251">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="d3e8c-252">![Prévisualiser les effets d’une opération de glisser-déplacer](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="d3e8c-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="d3e8c-253">Faites glisser le texte en dehors du contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="d3e8c-254">Le cercle passe du vert au bleu.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="d3e8c-255">Permettre à un panneau de recevoir des données déplacées</span><span class="sxs-lookup"><span data-stu-id="d3e8c-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="d3e8c-256">Dans cette section, vous permettez aux panneaux qui hébergent les contrôles utilisateur de cercle d’agir comme des cibles de déplacement pour les données de cercle glissées.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="d3e8c-257">Vous implémentez le code qui vous permet de déplacer un cercle d’un panneau vers un autre ou d’effectuer une copie d’un contrôle de cercle en maintenant enfoncée la touche CTRL tout en effectuant un glisser-déplacer d’un cercle.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="d3e8c-258">Pour permettre au panneau d’être une cible de déplacement</span><span class="sxs-lookup"><span data-stu-id="d3e8c-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="d3e8c-259">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="d3e8c-260">Comme indiqué dans le code XAML suivant, dans chacun de la <xref:System.Windows.Controls.StackPanel> contrôles, ajouter des gestionnaires pour les <xref:System.Windows.UIElement.DragOver> et <xref:System.Windows.UIElement.Drop> événements.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="d3e8c-261">Nom de la <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements, `panel_DragOver`et nommez le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="d3e8c-262">Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="d3e8c-263">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="d3e8c-264">Cela <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-265">Vérifie que les données glissées contiennent les données « Objet » qui a été créées dans le <xref:System.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l’appel à <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="d3e8c-266">Si les données « Object » sont présentes, vérifie si la touche CTRL est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="d3e8c-267">Si la touche CTRL, définit le <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="d3e8c-268">Sinon, la valeur du <xref:System.Windows.DragEventArgs.Effects%2A> propriété <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="d3e8c-269">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="d3e8c-270">Cela <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3e8c-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="d3e8c-271">Vérifie si le <xref:System.Windows.UIElement.Drop> événement a déjà été traité.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="d3e8c-272">Par exemple, si un cercle est déplacé sur un autre contrôle Circle qui gère la <xref:System.Windows.UIElement.Drop> événement, vous ne souhaitez pas que le panneau de configuration qui contient le cercle également le gérer.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="d3e8c-273">Si le <xref:System.Windows.UIElement.Drop> événement n'est pas géré, vérifie si la touche CTRL.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="d3e8c-274">Si la touche CTRL est activée lorsque le <xref:System.Windows.UIElement.Drop> se produit, effectue une copie du cercle de contrôle et l’ajouter à la <xref:System.Windows.Controls.Panel.Children%2A> collection de la <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="d3e8c-275">Si la touche CTRL n’est pas activée, déplace le cercle à partir de la <xref:System.Windows.Controls.Panel.Children%2A> collection de son panneau parent vers le <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau qui il a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="d3e8c-276">Définit le <xref:System.Windows.DragEventArgs.Effects%2A> propriété pour notifier le <xref:System.Windows.DragDrop.DoDragDrop%2A> (méthode) indique si une opération de déplacement ou de copie a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="d3e8c-277">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="d3e8c-278">Sélectionnez le texte `green` à partir de la <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="d3e8c-279">Faites glisser le texte sur un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="d3e8c-280">Faites glisser un contrôle de cercle du panneau gauche vers le panneau droit et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="d3e8c-281">Le cercle est supprimé de la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau gauche et ajouté à la collection Children du panneau droit.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="d3e8c-282">Faites glisser un contrôle de cercle du panneau dans lequel il se trouve vers l’autre panneau et déplacez-le en maintenant la touche CTRL enfoncée.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="d3e8c-283">Le cercle est copié et la copie est ajoutée à la <xref:System.Windows.Controls.Panel.Children%2A> collection du Panneau de réception.</span><span class="sxs-lookup"><span data-stu-id="d3e8c-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="d3e8c-284">![Glissement d'un cercle en maintenant la touche CTRL enfoncée](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="d3e8c-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e8c-285">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e8c-285">See Also</span></span>  
 [<span data-ttu-id="d3e8c-286">Vue d'ensemble du glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="d3e8c-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
