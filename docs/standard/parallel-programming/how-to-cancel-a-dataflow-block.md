---
title: "Comment : annuler un bloc de flux de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="5dd84-102">Comment : annuler un bloc de flux de données</span><span class="sxs-lookup"><span data-stu-id="5dd84-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="5dd84-103">Ce document montre comment activer l’annulation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5dd84-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="5dd84-104">Cet exemple utilise des Windows Forms pour montrer où les éléments de travail sont actifs dans un pipeline de flux de données, ainsi que les effets de l’annulation.</span><span class="sxs-lookup"><span data-stu-id="5dd84-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="5dd84-105">La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dd84-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="5dd84-106">Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="5dd84-107">Pour créer une Application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5dd84-107">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="5dd84-108">Créez un projet C# ou **Application Windows Forms** Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5dd84-108">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="5dd84-109">Dans les étapes suivantes, le projet est nommé `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-109">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="5dd84-110">Dans le Concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ajoutez un <xref:System.Windows.Forms.ToolStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="5dd84-110">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="5dd84-111">Ajouter un <xref:System.Windows.Forms.ToolStripButton> le contrôle à la <xref:System.Windows.Forms.ToolStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="5dd84-111">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5dd84-112">Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> et <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété **ajouter des éléments de travail**.</span><span class="sxs-lookup"><span data-stu-id="5dd84-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="5dd84-113">Ajoutez un deuxième <xref:System.Windows.Forms.ToolStripButton> le contrôle à la <xref:System.Windows.Forms.ToolStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="5dd84-113">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5dd84-114">Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, le <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété **Annuler**et le <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> propriété `False`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-114">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="5dd84-115">Ajoutez quatre <xref:System.Windows.Forms.ToolStripProgressBar> des objets sur le <xref:System.Windows.Forms.ToolStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="5dd84-115">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="5dd84-116">Création du pipeline de flux de données</span><span class="sxs-lookup"><span data-stu-id="5dd84-116">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="5dd84-117">Cette section décrit comment créer le pipeline de flux de données qui traite les éléments de travail et met à jour les barres de progression.</span><span class="sxs-lookup"><span data-stu-id="5dd84-117">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
#### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="5dd84-118">Pour créer le pipeline de flux de données</span><span class="sxs-lookup"><span data-stu-id="5dd84-118">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="5dd84-119">Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="5dd84-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="5dd84-120">Vérifiez que Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contient les `using` instructions (`Imports` dans les instructions [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5dd84-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="5dd84-121">Ajouter la classe `WorkItem` comme un type interne de la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-121">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="5dd84-122">Ajoutez les membres de données suivants à la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-122">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="5dd84-123">Ajoutez la méthode `CreatePipeline` suivante à la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="5dd84-123">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="5dd84-124">Étant donné que les blocs de flux de données `incrementProgress` et `decrementProgress` agissent sur l’interface utilisateur, il est important que ces actions se produisent sur le thread de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5dd84-124">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="5dd84-125">Pour ce faire, pendant la construction de ces objets, chacun d’eux fournit un <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objet ayant la <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriété <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5dd84-125">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5dd84-126">La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="5dd84-126">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="5dd84-127">Étant donné que le constructeur `Form1` est appelé depuis le thread de l’interface utilisateur, les actions des blocs de flux de données `incrementProgress` et `decrementProgress` fonctionnent aussi sur le thread de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5dd84-127">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="5dd84-128">Cet exemple définit le <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriété lorsqu’il construit les membres du pipeline.</span><span class="sxs-lookup"><span data-stu-id="5dd84-128">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="5dd84-129">Étant donné que le <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriété définitivement annulé l’exécution du bloc de flux de données, le pipeline entier doit être recréé une fois que l’utilisateur annule l’opération et souhaite ensuite ajouter plusieurs éléments de travail pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="5dd84-129">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="5dd84-130">Pour obtenir un exemple illustrant une autre méthode d’annulation d’un bloc de flux de données de sorte que les autres travaux puissent être effectués après l’annulation d’une opération, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md) (Procédure pas à pas : utilisation d’un flux de données dans une application Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="5dd84-130">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="5dd84-131">Connexion du pipeline de flux de données à l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="5dd84-131">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="5dd84-132">Cette section décrit comment connecter le pipeline de flux de données à l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5dd84-132">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="5dd84-133">La création du pipeline et l’ajout d’éléments de travail au pipeline sont contrôlés par le gestionnaire d’événements pour le bouton **Add Work Items** (Ajouter des éléments de travail).</span><span class="sxs-lookup"><span data-stu-id="5dd84-133">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="5dd84-134">L’annulation est lancée par le bouton **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="5dd84-134">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="5dd84-135">Lorsque l’utilisateur clique sur un de ces boutons, l’action appropriée est lancée de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="5dd84-135">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="5dd84-136">Pour connecter le pipeline de flux de données à l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="5dd84-136">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="5dd84-137">Dans le Concepteur de formulaires pour le formulaire principal, créez un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **ajouter des éléments de travail** bouton.</span><span class="sxs-lookup"><span data-stu-id="5dd84-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="5dd84-138">Implémentez la <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **ajouter des éléments de travail** bouton.</span><span class="sxs-lookup"><span data-stu-id="5dd84-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="5dd84-139">Dans le Concepteur de formulaires pour le formulaire principal, créez un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour le **Annuler** bouton.</span><span class="sxs-lookup"><span data-stu-id="5dd84-139">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="5dd84-140">Implémentez la <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour le **Annuler** bouton.</span><span class="sxs-lookup"><span data-stu-id="5dd84-140">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="5dd84-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="5dd84-141">Example</span></span>  
 <span data-ttu-id="5dd84-142">L'exemple suivant montre le code complet pour Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5dd84-142">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="5dd84-143">L'illustration suivante présente l'application en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5dd84-143">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="5dd84-144">![L’application Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="5dd84-144">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5dd84-145">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5dd84-145">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd84-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dd84-146">See Also</span></span>  
 [<span data-ttu-id="5dd84-147">Le flux de données</span><span class="sxs-lookup"><span data-stu-id="5dd84-147">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
