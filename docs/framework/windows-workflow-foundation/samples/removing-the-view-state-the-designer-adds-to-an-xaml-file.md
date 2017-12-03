---
title: "Suppression de l'état d'affichage que le concepteur ajoute à un fichier XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9f153d212e1180e5de92a6299d2fbb2d6864c42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="16356-102">Suppression de l'état d'affichage que le concepteur ajoute à un fichier XAML</span><span class="sxs-lookup"><span data-stu-id="16356-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="16356-103">Cet exemple montre comment créer une classe qui dérive de <xref:System.Windows.Markup.XamlWriter> et supprime l'état d'affichage d'un fichier XAML.</span><span class="sxs-lookup"><span data-stu-id="16356-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="16356-104"> écrit des informations dans le document XAML, qui est désigné sous le nom d'état d'affichage.</span><span class="sxs-lookup"><span data-stu-id="16356-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="16356-105">L'état d'affichage fait référence aux informations qui sont requises au moment du design, telles que le positionnement, et qui ne le sont pas au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="16356-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="16356-106"> insère ces informations dans le document XAML pendant qu'il est modifié.</span><span class="sxs-lookup"><span data-stu-id="16356-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="16356-107"> écrit l'état d'affichage dans le fichier XAML à l'aide de l'attribut `mc:Ignorable`, ces informations ne sont pas chargées lorsque le runtime charge le fichier XAML.</span><span class="sxs-lookup"><span data-stu-id="16356-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="16356-108">Cet exemple montre comment créer une classe qui supprime ces informations d'état d'affichage lors du traitement des nœuds XAML.</span><span class="sxs-lookup"><span data-stu-id="16356-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="16356-109">Discussion</span><span class="sxs-lookup"><span data-stu-id="16356-109">Discussion</span></span>  
 <span data-ttu-id="16356-110">Cet exemple montre comment créer un writer personnalisé.</span><span class="sxs-lookup"><span data-stu-id="16356-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="16356-111">Pour générer un writer XAML personnalisé, créez une classe qui hérite de <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="16356-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="16356-112">Comme les writers XAML sont souvent imbriqués, il est courant pour suivre un writer XAML « interne ».</span><span class="sxs-lookup"><span data-stu-id="16356-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="16356-113">Ces « interne » writers peuvent être considérés comme la référence à la pile restante de writers XAML, ce qui vous permet d’avoir plusieurs points d’entrée pour travailler, puis de déléguer le traitement au reste de la pile.</span><span class="sxs-lookup"><span data-stu-id="16356-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="16356-114">Dans cet exemple, quelques points sont intéressants.</span><span class="sxs-lookup"><span data-stu-id="16356-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="16356-115">L'un consiste à déterminer si l'élément qui est écrit provient de l'espace de noms d'un concepteur.</span><span class="sxs-lookup"><span data-stu-id="16356-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="16356-116">Notez que cela supprime également l'utilisation d'autres types de l'espace de noms du concepteur dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="16356-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
    return xamlMember.IsAttachable &&  
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
    this.InnerWriter = innerWriter;  
    this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
```  
  
 <span data-ttu-id="16356-117">Cela crée également une pile de membres XAML utilisés lors de la traversée du flux de nœud.</span><span class="sxs-lookup"><span data-stu-id="16356-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="16356-118">Le travail restant de cet exemple est en grande partie contenu dans le <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` (méthode).</span><span class="sxs-lookup"><span data-stu-id="16356-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
```csharp
public override void WriteStartMember(XamlMember xamlMember)  
{  
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))  
    {  
        m_attachedPropertyDepth++;  
    }  
  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteStartMember(xamlMember);  
}  
```  
  
 <span data-ttu-id="16356-119">Les méthodes suivantes vérifient ensuite leur présence dans un conteneur d'états d'affichage et, le cas échéant, retournent et ne transmettent pas le nœud à la pile de writers.</span><span class="sxs-lookup"><span data-stu-id="16356-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
```csharp
public override void WriteValue(Object value)  
{  
    if (m_attachedPropertyDepth > 0)  
    {  
        return;  
    }  
  
    InnerWriter.WriteValue(value);  
}  
```  
  
 <span data-ttu-id="16356-120">Pour utiliser un writer XAML personnalisé, vous devez le lier à une pile de writers XAML.</span><span class="sxs-lookup"><span data-stu-id="16356-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="16356-121">Le code suivant montre comment il peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="16356-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="16356-122">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="16356-122">To use this sample</span></span>  
  
1. <span data-ttu-id="16356-123">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="16356-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="16356-124">Ouvrez une invite de commandes et naviguez jusqu'au répertoire où ViewStageCleaningWriter.exe est généré.</span><span class="sxs-lookup"><span data-stu-id="16356-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="16356-125">Exécutez ViewStateCleaningWriter.exe sur le fichier Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="16356-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="16356-126">La syntaxe pour le fichier exécutable est affichée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="16356-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="16356-127">Cela génère un fichier XAML à \[outfile], qui a toutes ses informations d’état de vue supprimées.</span><span class="sxs-lookup"><span data-stu-id="16356-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16356-128">Pour un workflow <xref:System.Activities.Statements.Sequence>, plusieurs indicateurs de virtualisation sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="16356-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="16356-129">Le concepteur doit donc recalculer la disposition lors du chargement suivant.</span><span class="sxs-lookup"><span data-stu-id="16356-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="16356-130">Lorsque vous utilisez cet exemple pour un <xref:System.Activities.Statements.Flowchart>, toutes les informations de routage de positionnement et de ligne sont supprimées et, lors du chargement suivant dans le concepteur, toutes les activités sont empilées sur le côté gauche de l'écran.</span><span class="sxs-lookup"><span data-stu-id="16356-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="16356-131">Pour créer un exemple de fichier XAML à utiliser avec cet exemple</span><span class="sxs-lookup"><span data-stu-id="16356-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="16356-132">Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16356-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="16356-133">Créez une application console de workflow.</span><span class="sxs-lookup"><span data-stu-id="16356-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="16356-134">Faites glisser quelques activités sur la zone de dessin.</span><span class="sxs-lookup"><span data-stu-id="16356-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="16356-135">Enregistrez le fichier XAML de workflow.</span><span class="sxs-lookup"><span data-stu-id="16356-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="16356-136">Inspectez le fichier XAML pour consulter les propriétés jointes d'état d'affichage.</span><span class="sxs-lookup"><span data-stu-id="16356-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="16356-137">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="16356-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="16356-138">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="16356-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="16356-139">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="16356-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16356-140">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="16356-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
