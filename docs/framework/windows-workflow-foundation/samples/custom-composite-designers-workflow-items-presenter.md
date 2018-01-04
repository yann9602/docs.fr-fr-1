---
title: "Concepteurs composites personnalisés - Présentateur d'éléments de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78f21887ab4a43e13984f2460435e862dfb702f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="5adb9-102">Concepteurs composites personnalisés - Présentateur d'éléments de workflow</span><span class="sxs-lookup"><span data-stu-id="5adb9-102">Custom Composite Designers - Workflow Items Presenter</span></span>
<span data-ttu-id="5adb9-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> est un type de clé dans le modèle de programmation de concepteur WF qui permet la modification d'une collection d'éléments contenus.</span><span class="sxs-lookup"><span data-stu-id="5adb9-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="5adb9-104">Cet exemple montre comment générer un concepteur d'activités qui expose une telle collection modifiable.</span><span class="sxs-lookup"><span data-stu-id="5adb9-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>  
  
 <span data-ttu-id="5adb9-105">Cet exemple illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5adb9-105">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="5adb9-106">Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5adb9-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="5adb9-107">Création d’un concepteur d’activités avec une vue « réduite » et « développée ».</span><span class="sxs-lookup"><span data-stu-id="5adb9-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>  
  
-   <span data-ttu-id="5adb9-108">Substitution d'un concepteur par défaut dans une application réhébergée.</span><span class="sxs-lookup"><span data-stu-id="5adb9-108">Overriding a default designer in a rehosted application.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5adb9-109">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5adb9-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5adb9-110">Ouvrez le **UsingWorkflowItemsPresenter.sln** exemple de solution pour c# ou VB dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5adb9-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5adb9-111">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="5adb9-111">Build and run the solution.</span></span> <span data-ttu-id="5adb9-112">Une application de concepteur de workflow réhébergée doit s'ouvrir, et vous pouvez faire glisser des activités sur la zone de dessin.</span><span class="sxs-lookup"><span data-stu-id="5adb9-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>  
  
## <a name="sample-highlights"></a><span data-ttu-id="5adb9-113">Points clés de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5adb9-113">Sample Highlights</span></span>  
 <span data-ttu-id="5adb9-114">Le code de cet exemple illustre les points suivants :</span><span class="sxs-lookup"><span data-stu-id="5adb9-114">The code for this sample shows the following:</span></span>  
  
-   <span data-ttu-id="5adb9-115">L'activité pour laquelle un concepteur est conçu : `Parallel`</span><span class="sxs-lookup"><span data-stu-id="5adb9-115">The activity a designer is built for:  `Parallel`</span></span>  
  
-   <span data-ttu-id="5adb9-116">La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5adb9-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5adb9-117">Quelques points à noter :</span><span class="sxs-lookup"><span data-stu-id="5adb9-117">A few things to point out:</span></span>  
  
    -   <span data-ttu-id="5adb9-118">Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="5adb9-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="5adb9-119">`ModelItem` est la propriété sur `WorkflowElementDesigner` qui fait référence à l'objet sous-jacent pour lequel le concepteur est utilisé, dans ce cas, `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="5adb9-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>  
  
    -   <span data-ttu-id="5adb9-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> peut être utilisé pour placer un visuel à afficher entre les éléments individuels de la collection.</span><span class="sxs-lookup"><span data-stu-id="5adb9-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>  
  
    -   <span data-ttu-id="5adb9-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> est un modèle qui peut être fourni pour déterminer la disposition des éléments dans la collection.</span><span class="sxs-lookup"><span data-stu-id="5adb9-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="5adb9-122">Dans le cas présent, un panneau d'empilement horizontal est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5adb9-122">In this case, a horizontal stack panel is used.</span></span>  
  
 <span data-ttu-id="5adb9-123">L'exemple de code suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="5adb9-123">This following example code shows this.</span></span>  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
```  
  
-   <span data-ttu-id="5adb9-124">Effectuez une association de `DesignerAttribute` au type `Parallel`, puis fournissez en sortie les attributs signalés.</span><span class="sxs-lookup"><span data-stu-id="5adb9-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>  
  
    -   <span data-ttu-id="5adb9-125">En premier lieu, enregistrez tous les concepteurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="5adb9-125">First, register all of the default designers.</span></span>  
  
 <span data-ttu-id="5adb9-126">Voici l'exemple de code.</span><span class="sxs-lookup"><span data-stu-id="5adb9-126">The following is the code example.</span></span>  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
```  
  
    -   <span data-ttu-id="5adb9-127">Ensuite, substituez la parallèle dans la méthode `RegisterCustomMetadata`.</span><span class="sxs-lookup"><span data-stu-id="5adb9-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>  
  
 <span data-ttu-id="5adb9-128">Le code suivant illustre ce point en C# et en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5adb9-128">The following code shows this in C# and Visual Basic.</span></span>  
 
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
```  
  
-   <span data-ttu-id="5adb9-129">Enfin, notez l'utilisation de modèles de données et de déclencheurs différents pour sélectionner le modèle approprié en fonction de la propriété `IsRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="5adb9-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>  
  
 <span data-ttu-id="5adb9-130">Voici l'exemple de code.</span><span class="sxs-lookup"><span data-stu-id="5adb9-130">The following is the code example.</span></span>  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="5adb9-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5adb9-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5adb9-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5adb9-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5adb9-133">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5adb9-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5adb9-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5adb9-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="5adb9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5adb9-135">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [<span data-ttu-id="5adb9-136">Développement d’applications avec le Concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="5adb9-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
