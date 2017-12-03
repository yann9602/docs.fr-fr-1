---
title: "Tâche 2 : héberger le Workflow Designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fffc934bbbd1fc707e0bf5c0afbf79a40fc8c633
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="34f52-102">Tâche 2 : héberger le Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="34f52-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="34f52-103">Cette rubrique décrit la procédure d'hébergement d'une instance du [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dans une application [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34f52-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application.</span></span>  
  
 <span data-ttu-id="34f52-104">La procédure configure le **grille** contrôle qui contient le concepteur, crée par programmation une instance de la <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une valeur par défaut <xref:System.Activities.Statements.Sequence> activité, inscrit pour fournir les métadonnées du Concepteur prise en charge du concepteur pour des ordinateurs hôtes et des activités intégrées tous les le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans le [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="34f52-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="34f52-105">Pour héberger le concepteur de workflow</span><span class="sxs-lookup"><span data-stu-id="34f52-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="34f52-106">Ouvrez la HostingApplication de projet que vous avez créé dans [tâche 1 : créer une Application Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="34f52-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="34f52-107">Pour faciliter l'utilisation du [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ajustez la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="34f52-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="34f52-108">Pour ce faire, sélectionnez **MainWindow** dans le concepteur, appuyez sur F4 pour afficher la **propriétés** fenêtre, puis, dans le **disposition** section, définissez la **largeur** à une valeur de 600 et la **hauteur** à une valeur de 350.</span><span class="sxs-lookup"><span data-stu-id="34f52-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="34f52-109">Définir le nom de la grille en sélectionnant le **grille** Panneau de configuration dans le concepteur (cliquez sur la zone à l’intérieur de la **MainWindow**) et en définissant le **nom** propriété en haut de la  **Propriétés** fenêtre valeur « grid1 ».</span><span class="sxs-lookup"><span data-stu-id="34f52-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="34f52-110">Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) à côté du `ColumnDefinitions` propriété pour ouvrir la **éditeur de collections** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="34f52-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="34f52-111">Dans le **éditeur de collections** boîte de dialogue, cliquez sur le **ajouter** trois fois pour insérer trois colonnes dans la disposition.</span><span class="sxs-lookup"><span data-stu-id="34f52-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="34f52-112">La première colonne contiendra la **boîte à outils**, la deuxième colonne hébergera le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], et la troisième colonne sera utilisée pour l’inspecteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="34f52-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="34f52-113">Définir le `Width` propriété de la colonne du milieu à la valeur « 4 * ».</span><span class="sxs-lookup"><span data-stu-id="34f52-113">Set the `Width` property of the middle column to the value "4*".</span></span>  
  
7.  <span data-ttu-id="34f52-114">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="34f52-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="34f52-115">Le XAML suivant est ajouté à votre fichier MainWindow.xaml :</span><span class="sxs-lookup"><span data-stu-id="34f52-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="34f52-116">Dans **l’Explorateur de solutions**, avec le bouton droit de MainWindow.xaml et sélectionnez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="34f52-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="34f52-117">Modifiez le code en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="34f52-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="34f52-118">Ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="34f52-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="34f52-119">Pour déclarer un champ de membre privé devant contenir une instance de <xref:System.Activities.Presentation.WorkflowDesigner>, ajoutez le code suivant à la classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="34f52-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
        ```csharp  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
        ```  
  
    3.  <span data-ttu-id="34f52-120">Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="34f52-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="34f52-121">L’implémentation crée une instance de la <xref:System.Activities.Presentation.WorkflowDesigner>, ajoute un <xref:System.Activities.Statements.Sequence> activité et le place dans la colonne du milieu de la grid1 **grille**.</span><span class="sxs-lookup"><span data-stu-id="34f52-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
        ```csharp  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
        ```  
  
    4.  <span data-ttu-id="34f52-122">Pour ajouter la prise en charge du concepteur pour toutes les activités intégrées, enregistrez les métadonnées du concepteur.</span><span class="sxs-lookup"><span data-stu-id="34f52-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="34f52-123">Cela vous permet de déplacer des activités, de la boîte à outils vers l'activité <xref:System.Activities.Statements.Sequence> d'origine dans le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34f52-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="34f52-124">Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="34f52-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="34f52-125">l’inscription des concepteurs d’activités, consultez [Comment : créer un concepteur d’activités personnalisé](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="34f52-125"> registering activity designers, see [How to: Create a Custom Activity Designer](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="34f52-126">Dans le constructeur de classes `MainWindow`, ajoutez des appels aux méthodes précédemment déclarées pour enregistrer les métadonnées dans le but de la prise en charge du concepteur et pour créer l'objet <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="34f52-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="34f52-127">La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="34f52-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="34f52-128">Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.</span><span class="sxs-lookup"><span data-stu-id="34f52-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="34f52-129">Pour générer et exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="34f52-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="34f52-130">Consultez [tâche 3 : créer les volets de PropertyGrid et boîte à outils](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) pour savoir comment ajouter **boîte à outils** et **PropertyGrid** prend en charge à votre Concepteur de workflow réhébergé.</span><span class="sxs-lookup"><span data-stu-id="34f52-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f52-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f52-131">See Also</span></span>  
 [<span data-ttu-id="34f52-132">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="34f52-132">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="34f52-133">Tâche 1 : Créer une nouvelle application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="34f52-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="34f52-134">Tâche 3 : Créer les volets Toolbox et PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="34f52-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
