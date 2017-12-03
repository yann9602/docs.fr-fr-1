---
title: "Création d'une activité en cours d'exécution avec DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d40fe3601cb8ad7c4f77cf50825da1deace5644e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="d6d2f-102">Création d'une activité en cours d'exécution avec DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="d6d2f-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="d6d2f-103"><xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="d6d2f-104"><xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="d6d2f-105">Fonctionnalités DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="d6d2f-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="d6d2f-106">L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="d6d2f-107">Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="d6d2f-108">En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="d6d2f-109">En XAML, ils sont déclarés à l'aide de balises `x:Class` et `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="d6d2f-110">Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="d6d2f-111">Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="d6d2f-112">Pour créer une activité au moment de l'exécution à l'aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="d6d2f-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="d6d2f-113">Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6d2f-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d6d2f-114">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="d6d2f-115">Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="d6d2f-116">Sélectionnez **Application Console de Workflow séquentiel** dans les **modèles** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="d6d2f-117">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="d6d2f-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="d6d2f-118">Cliquez sur Workflow1.xaml dans le projet HelloActivity et sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="d6d2f-119">Ouvrez Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-119">Open Program.cs.</span></span> <span data-ttu-id="d6d2f-120">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="d6d2f-121">Remplacez le contenu de la méthode `Main` par le code ci-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  <span data-ttu-id="d6d2f-122">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-122">Execute the application.</span></span> <span data-ttu-id="d6d2f-123">Une fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="d6d2f-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="d6d2f-124">affiche.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="d6d2f-125">Pour créer une activité au moment de l'exécution à l'aide de XAML</span><span class="sxs-lookup"><span data-stu-id="d6d2f-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="d6d2f-126">Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6d2f-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d6d2f-127">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="d6d2f-128">Sélectionnez **Workflow 4.0** sous **Visual C#** dans les **Types de projets** , puis sélectionnez le **v2010** nœud.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="d6d2f-129">Sélectionnez **Application Console de Workflow** dans les **modèles** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="d6d2f-130">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="d6d2f-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="d6d2f-131">Dans le projet HelloActivity, ouvrez Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="d6d2f-132">Cliquez sur le **Arguments** option au bas du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="d6d2f-133">Créez un argument `In` appelé `TextToWrite` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="d6d2f-134">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la boîte à outils vers l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="d6d2f-135">Affectez la valeur `TextToWrite` à la **texte** propriété de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="d6d2f-136">Ouvrez Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-136">Open Program.cs.</span></span> <span data-ttu-id="d6d2f-137">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="d6d2f-138">Remplacez le contenu de la méthode `Main` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d6d2f-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="d6d2f-139">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-139">Execute the application.</span></span> <span data-ttu-id="d6d2f-140">Une fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="d6d2f-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="d6d2f-141">s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-141">appears.</span></span>  
  
8.  <span data-ttu-id="d6d2f-142">Cliquez sur le fichier Workflow1.xaml dans le **l’Explorateur de solutions** et sélectionnez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="d6d2f-143">Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="d6d2f-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d2f-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6d2f-144">See Also</span></span>  
 [<span data-ttu-id="d6d2f-145">Création de workflows, d’activités et d’expressions à l’aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="d6d2f-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [<span data-ttu-id="d6d2f-146">Création avec DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="d6d2f-146">DynamicActivity Creation</span></span>](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
