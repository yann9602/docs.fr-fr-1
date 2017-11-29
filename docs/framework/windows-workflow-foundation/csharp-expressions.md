---
title: Expressions C#
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7d62d147bdc0177a28dbcc7d235f1c48dc51460
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="c-expressions"></a><span data-ttu-id="d992f-102">Expressions C#</span><span class="sxs-lookup"><span data-stu-id="d992f-102">C# Expressions</span></span>
<span data-ttu-id="d992f-103">À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les expressions C# sont prises en charge dans [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d992f-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="d992f-104">Les nouveaux projets de workflow en C# créés dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] qui ciblent le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] utilisent les expressions C# et les projets de workflow en Visual Basic utilisent les expressions Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d992f-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="d992f-105">Les projets de workflow [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] qui utilisent des expressions Visual Basic peuvent être migrés vers [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] indépendamment du langage de projet et sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d992f-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="d992f-106">Cette rubrique fournit une vue d'ensemble des expressions C# dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d992f-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="d992f-107">Utilisation des expressions C# dans les workflows</span><span class="sxs-lookup"><span data-stu-id="d992f-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="d992f-108">À l’aide d’expressions c# dans le Concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="d992f-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="d992f-109">Descendante compatibilité</span><span class="sxs-lookup"><span data-stu-id="d992f-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="d992f-110">À l’aide d’expressions c# dans les workflows de code</span><span class="sxs-lookup"><span data-stu-id="d992f-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="d992f-111">À l’aide d’expressions c# dans les workflows XAML</span><span class="sxs-lookup"><span data-stu-id="d992f-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="d992f-112">Xaml compilé</span><span class="sxs-lookup"><span data-stu-id="d992f-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="d992f-113">Xaml libre</span><span class="sxs-lookup"><span data-stu-id="d992f-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="d992f-114">À l’aide d’expressions c# dans les services de workflow XAMLX</span><span class="sxs-lookup"><span data-stu-id="d992f-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <span data-ttu-id="d992f-115"><a name="WFDesigner"></a>À l’aide d’expressions c# dans le Concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="d992f-115"><a name="WFDesigner"></a> Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="d992f-116">À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les expressions C# sont prises en charge dans [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d992f-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="d992f-117">Les projets de workflow en C# créés dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] qui ciblent le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] utilisent les expressions C# et les projets de workflow en Visual Basic utilisent les expressions Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d992f-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="d992f-118">Pour spécifier l’expression c# souhaitée, tapez-la dans la zone intitulée **entrer une expression c#**.</span><span class="sxs-lookup"><span data-stu-id="d992f-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="d992f-119">Cette étiquette s'affiche dans la fenêtre de propriétés lorsque l'activité est sélectionnée dans le concepteur, ou sur l'activité dans Workflow Designer.</span><span class="sxs-lookup"><span data-stu-id="d992f-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="d992f-120">Dans l'exemple suivant, deux activités `WriteLine` sont contenues dans `Sequence` à l'intérieur de `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="d992f-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="d992f-121">![Activité sequence créée automatiquement](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="d992f-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d992f-122">Les expressions C# sont prises en charge uniquement dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], et ne sont pas prises en charge dans le concepteur de workflow réhébergé.</span><span class="sxs-lookup"><span data-stu-id="d992f-122">C# expressions are supported only in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d992f-123">nouvelles fonctionnalités WF45 pris en charge dans le concepteur réhébergé, consultez [prise en charge de nouvelles Workflow Foundation 4.5 dans le Concepteur de Workflow réhébergés](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d992f-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <span data-ttu-id="d992f-124"><a name="BackwardCompat"></a>Descendante compatibilité</span><span class="sxs-lookup"><span data-stu-id="d992f-124"><a name="BackwardCompat"></a> Backwards compatibility</span></span>  
 <span data-ttu-id="d992f-125">Les expressions Visual Basic dans les projets de workflow C# [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] existants qui ont été migrés vers [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="d992f-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="d992f-126">Lorsque les expressions Visual Basic sont affichées dans le Concepteur de flux de travail, le texte de l’expression Visual Basic existant est remplacé par **valeur a été définie en XAML**, sauf si l’expression Visual Basic est une syntaxe c# valide.</span><span class="sxs-lookup"><span data-stu-id="d992f-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="d992f-127">Si l'expression Visual Basic correspond à une syntaxe C# valide, elle s'affiche.</span><span class="sxs-lookup"><span data-stu-id="d992f-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="d992f-128">Pour mettre à jour les expressions Visual Basic en C#, modifiez-les dans le concepteur de workflow et spécifiez l'expression C# équivalente.</span><span class="sxs-lookup"><span data-stu-id="d992f-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="d992f-129">Il n'est pas nécessaire de mettre à jour les expressions Visual Basic vers C#, mais une fois les expressions mises à jour dans le concepteur de workflow, elles sont converties en C# et ne peuvent pas être rétablies en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d992f-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <span data-ttu-id="d992f-130"><a name="CodeWorkflows"></a>À l’aide d’expressions c# dans les workflows de code</span><span class="sxs-lookup"><span data-stu-id="d992f-130"><a name="CodeWorkflows"></a> Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="d992f-131">Les expressions C# sont prises en charge dans les workflows basés sur du code [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], mais vous devez compiler les expressions C# à l'aide de <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> pour pouvoir appeler le workflow.</span><span class="sxs-lookup"><span data-stu-id="d992f-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d992f-132">Les auteurs de workflow peuvent utiliser `CSharpValue` comme r-value dans une expression, et `CSharpReference` comme l-value dans une expression.</span><span class="sxs-lookup"><span data-stu-id="d992f-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="d992f-133">Dans l'exemple suivant, un workflow qui contient une activité `Assign` est créé et une activité consistant en une activité `WriteLine` est contenue dans une activité `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="d992f-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="d992f-134">`CSharpReference` est spécifié pour l'argument `To` de l'activité `Assign`, et est utilisé comme l-value de l'expression.</span><span class="sxs-lookup"><span data-stu-id="d992f-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="d992f-135">`CSharpValue` est spécifié pour l'argument `Value` d'`Assign`, et pour l'argument `Text` de `WriteLine`, et est utilisé comme r-value de ces deux expressions.</span><span class="sxs-lookup"><span data-stu-id="d992f-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
```csharp  
Variable<int> n = new Variable<int>  
{  
    Name = "n"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { n },  
    Activities =  
    {  
        new Assign<int>  
        {  
            To = new CSharpReference<int>("n"),  
            Value = new CSharpValue<int>("new Random().Next(1, 101)")  
        },  
        new WriteLine  
        {  
            Text = new CSharpValue<string>("\"The number is \" + n")  
        }  
    }  
};  
  
CompileExpressions(wf);  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="d992f-136">Une fois que le workflow soit construit, les expressions C# sont compilées en appelant la méthode d'assistance `CompileExpressions`, puis le workflow.</span><span class="sxs-lookup"><span data-stu-id="d992f-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="d992f-137">L'exemple suivant utilise la méthode `CompileExpressions`.</span><span class="sxs-lookup"><span data-stu-id="d992f-137">The following example is the `CompileExpressions` method.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="d992f-138">Si les expressions c# ne sont pas compilées, une <xref:System.NotSupportedException> est levée lorsque le workflow est appelé avec un message semblable au suivant : `Expression Activity type 'CSharpValue`1' requiert une compilation pour pouvoir pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d992f-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="d992f-139">Veuillez vous assurer que le flux de travail a été compilé. »</span><span class="sxs-lookup"><span data-stu-id="d992f-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="d992f-140">Si votre workflow basé sur du code personnalisé utilise `DynamicActivity`, vous devez apporter des modifications à la méthode `CompileExpressions`, tel que l'indique l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="d992f-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
```csharp  
static void CompileExpressions(DynamicActivity dynamicActivity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions. For Dynamic Activities this can be retrieved using the  
    // name property , which must be in the form Namespace.Type.  
    string activityName = dynamicActivity.Name;  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = dynamicActivity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = true  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(  
        dynamicActivity, compiledExpressionRoot);  
}  
```  
  
 <span data-ttu-id="d992f-141">Il existe plusieurs différences dans la surcharge de `CompileExpressions` qui compile les expressions C# dans une activité dynamique.</span><span class="sxs-lookup"><span data-stu-id="d992f-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="d992f-142">Le paramètre `CompileExpressions` a la valeur `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="d992f-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="d992f-143">Le nom de type et l'espace de noms sont récupérés à l'aide de la propriété `DynamicActivity.Name`.</span><span class="sxs-lookup"><span data-stu-id="d992f-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="d992f-144">`TextExpressionCompilerSettings.ForImplementation` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d992f-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="d992f-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` est appelé au lieu de `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="d992f-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d992f-146">utilisation des expressions dans le code, consultez [création de Workflows, des activités et des Expressions à l’aide d’impératif Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="d992f-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <span data-ttu-id="d992f-147"><a name="XamlWorkflows"></a>À l’aide d’expressions c# dans les workflows XAML</span><span class="sxs-lookup"><span data-stu-id="d992f-147"><a name="XamlWorkflows"></a> Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="d992f-148">Les expressions C# sont prises en charge dans les workflows XAML.</span><span class="sxs-lookup"><span data-stu-id="d992f-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="d992f-149">Les workflows XAML compilés sont compilés en un type, et workflows XAML libre sont chargés par le runtime et compilés dans une arborescence d’activité lorsque le workflow est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d992f-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="d992f-150">Xaml compilé</span><span class="sxs-lookup"><span data-stu-id="d992f-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="d992f-151">Xaml libre</span><span class="sxs-lookup"><span data-stu-id="d992f-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <span data-ttu-id="d992f-152"><a name="CompiledXaml"></a>Xaml compilé</span><span class="sxs-lookup"><span data-stu-id="d992f-152"><a name="CompiledXaml"></a> Compiled Xaml</span></span>  
 <span data-ttu-id="d992f-153">Les expressions C# sont prises en charge dans les workflows XAML compilés qui sont compilés en un type dans le cadre d'un projet de workflow C# qui cible [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d992f-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="d992f-154">XAML compilé est le type par défaut de création de workflow dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], et les projets de workflow C# créés dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] qui ciblent [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] utilisent les expressions C#.</span><span class="sxs-lookup"><span data-stu-id="d992f-154">Compiled XAML is the default type of workflow authoring in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and C# workflow projects created in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <span data-ttu-id="d992f-155"><a name="LooseXaml"></a>Xaml libre</span><span class="sxs-lookup"><span data-stu-id="d992f-155"><a name="LooseXaml"></a> Loose Xaml</span></span>  
 <span data-ttu-id="d992f-156">Les expressions C# sont prises en charge dans les workflows XAML libre.</span><span class="sxs-lookup"><span data-stu-id="d992f-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="d992f-157">Le programme d'hôte de workflow qui charge et appelle le workflow XAML libre doit cibler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], et <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> doit avoir la valeur `true` (la valeur par défaut est `false`).</span><span class="sxs-lookup"><span data-stu-id="d992f-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="d992f-158">Pour affecter la valeur <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> à `true`, créez une instance <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> dont la propriété <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> a la valeur `true`, et passez-la comme paramètre à <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d992f-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d992f-159">Si `CompileExpressions` n’est pas définie `true`, un <xref:System.NotSupportedException> sera levée avec un message semblable au suivant : `Expression Activity type 'CSharpValue`1' requiert une compilation pour pouvoir pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="d992f-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="d992f-160">Veuillez vous assurer que le flux de travail a été compilé. »</span><span class="sxs-lookup"><span data-stu-id="d992f-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d992f-161">utilisation de workflows en XAML, consultez [sérialisation de Workflows et les activités vers et depuis XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d992f-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <span data-ttu-id="d992f-162"><a name="WFServices"></a>À l’aide d’expressions c# dans les services de workflow XAMLX</span><span class="sxs-lookup"><span data-stu-id="d992f-162"><a name="WFServices"></a> Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="d992f-163">Les expressions C# sont prises en charge dans les services de workflow XAMLX.</span><span class="sxs-lookup"><span data-stu-id="d992f-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="d992f-164">Lorsqu'un service de workflow est hébergé dans IIS ou WAS, aucune étape supplémentaire n'est nécessaire, mais si le service de workflow XAML est auto-hébergé, les expressions C# doivent être compilées.</span><span class="sxs-lookup"><span data-stu-id="d992f-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="d992f-165">Pour compiler les expressions c# dans un service de workflow auto-hébergé XAMLX, d’abord charger le fichier XAMLX dans un `WorkflowService`, puis passez le `Body` du `WorkflowService` à la `CompileExpressions` méthode décrite dans la précédente [à l’aide de c# expressions dans les workflows de code](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span><span class="sxs-lookup"><span data-stu-id="d992f-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="d992f-166">Dans l'exemple suivant, un service de workflow XAMLX est chargé, les expressions C# sont compilées, puis le service de workflow est ouvert et attend des demandes.</span><span class="sxs-lookup"><span data-stu-id="d992f-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
```csharp  
// Load the XAMLX workflow service.  
WorkflowService workflow1 =  
    (WorkflowService)XamlServices.Load(xamlxPath);  
  
// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.  
CompileExpressions(workflow1.Body);  
  
// Initialize the WorkflowServiceHost.  
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));  
  
// Enable Metadata publishing/  
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
smb.HttpGetEnabled = true;  
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;  
host.Description.Behaviors.Add(smb);  
  
// Open the WorkflowServiceHost and wait for requests.  
host.Open();  
Console.WriteLine("Press enter to quit");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="d992f-167">Si les expressions C# ne sont pas compilées, l'opération `Open` réussit, mais le workflow échoue lorsqu'il est appelé.</span><span class="sxs-lookup"><span data-stu-id="d992f-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="d992f-168">Les éléments suivants `CompileExpressions` méthode est identique à la méthode à partir de la précédente [expressions à l’aide de c# dans les workflows avec code](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span><span class="sxs-lookup"><span data-stu-id="d992f-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
```csharp  
static void CompileExpressions(Activity activity)  
{  
    // activityName is the Namespace.Type of the activity that contains the  
    // C# expressions.  
    string activityName = activity.GetType().ToString();  
  
    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name  
    // to represent the new type that represents the compiled expressions.  
    // Take everything after the last . for the type name.  
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";  
    // Take everything before the last . for the namespace.  
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());  
  
    // Create a TextExpressionCompilerSettings.  
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings  
    {  
        Activity = activity,  
        Language = "C#",  
        ActivityName = activityType,  
        ActivityNamespace = activityNamespace,  
        RootNamespace = null,  
        GenerateAsPartialClass = false,  
        AlwaysGenerateSource = true,  
        ForImplementation = false  
    };  
  
    // Compile the C# expression.  
    TextExpressionCompilerResults results =  
        new TextExpressionCompiler(settings).Compile();  
  
    // Any compilation errors are contained in the CompilerMessages.  
    if (results.HasErrors)  
    {  
        throw new Exception("Compilation failed.");  
    }  
  
    // Create an instance of the new compiled expression type.  
    ICompiledExpressionRoot compiledExpressionRoot =  
        Activator.CreateInstance(results.ResultType,  
            new object[] { activity }) as ICompiledExpressionRoot;  
  
    // Attach it to the activity.  
    CompiledExpressionInvoker.SetCompiledExpressionRoot(  
        activity, compiledExpressionRoot);  
}  
```
