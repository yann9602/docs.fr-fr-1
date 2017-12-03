---
title: "Sérialisation de workflows et d'activités vers et à partir de XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be1c85a87896c176d5e81d2938418194d28b93b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="21dc0-102">Sérialisation de workflows et d'activités vers et à partir de XAML</span><span class="sxs-lookup"><span data-stu-id="21dc0-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="21dc0-103">Outre le fait d'être compilées en types qui sont contenus dans des assemblys, les définitions de workflow peuvent également être sérialisées en XAML.</span><span class="sxs-lookup"><span data-stu-id="21dc0-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="21dc0-104">Ces définitions sérialisées peuvent être rechargées pour la modification ou l'inspection, passées à un système de génération pour la compilation, ou bien chargées et appelées.</span><span class="sxs-lookup"><span data-stu-id="21dc0-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="21dc0-105">Cette rubrique fournit une vue d'ensemble de la sérialisation de définitions de workflow et de l'utilisation de définitions de workflow XAML.</span><span class="sxs-lookup"><span data-stu-id="21dc0-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="21dc0-106">Utilisation de définitions de workflow XAML</span><span class="sxs-lookup"><span data-stu-id="21dc0-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="21dc0-107">Pour créer une définition de workflow pour la sérialisation, la classe <xref:System.Activities.ActivityBuilder> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="21dc0-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="21dc0-108">La création d'un <xref:System.Activities.ActivityBuilder> est très semblable à la création d'un <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="21dc0-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="21dc0-109">Tous les arguments souhaités sont spécifiés, et les activités qui constituent le comportement sont configurées.</span><span class="sxs-lookup"><span data-stu-id="21dc0-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="21dc0-110">Dans l'exemple suivant, une activité `Add` qui prend deux arguments d'entrée est créée, elle les ajoute, puis le résultat.</span><span class="sxs-lookup"><span data-stu-id="21dc0-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="21dc0-111">Étant donné que cette activité retourne un résultat, la classe <xref:System.Activities.ActivityBuilder%601> générique est utilisée.</span><span class="sxs-lookup"><span data-stu-id="21dc0-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="21dc0-112">Chacune des instances <xref:System.Activities.DynamicActivityProperty> représente l'un des arguments d'entrée du workflow, et <xref:System.Activities.ActivityBuilder.Implementation%2A> contient les activités qui composent la logique du workflow.</span><span class="sxs-lookup"><span data-stu-id="21dc0-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="21dc0-113">Notez que les expressions r-value dans cet exemple sont des expressions Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21dc0-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="21dc0-114">Les expressions lambda ne sont pas sérialisables en XAML à moins d'utiliser <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>.</span><span class="sxs-lookup"><span data-stu-id="21dc0-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="21dc0-115">Si les workflows sérialisés sont destinés à être ouverts ou modifiés dans le concepteur de workflow, des expressions Visual Basic doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="21dc0-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="21dc0-116">[Création de flux de travail, des activités et des Expressions à l’aide du Code impératif](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="21dc0-116"> [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="21dc0-117">Pour sérialiser la définition de workflow représentée par l'instance <xref:System.Activities.ActivityBuilder> en XAML, utilisez <xref:System.Activities.XamlIntegration.ActivityXamlServices> de créer <xref:System.Xaml.XamlWriter>, puis utilisez <xref:System.Xaml.XamlServices> pour sérialiser la définition de workflow à l'aide de <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="21dc0-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="21dc0-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> a des méthodes pour mapper des instances <xref:System.Activities.ActivityBuilder> vers et à partir du XAML, et pour charger des workflows XAML et retourner un <xref:System.Activities.DynamicActivity> qui peut être appelé.</span><span class="sxs-lookup"><span data-stu-id="21dc0-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="21dc0-119">Dans l'exemple suivant, l'instance <xref:System.Activities.ActivityBuilder> de l'exemple précédent est sérialisée en chaîne, et également enregistrée dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="21dc0-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="21dc0-120">L'exemple suivant représente le workflow sérialisé.</span><span class="sxs-lookup"><span data-stu-id="21dc0-120">The following example represents the serialized workflow.</span></span>  
  
```xaml  
<Activity   
  x:TypeArguments="x:Int32"   
  x:Class="Add"   
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />  
  </x:Members>  
  <Sequence>  
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />  
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">  
      <Assign.To>  
        <OutArgument x:TypeArguments="x:Int32">  
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />  
          </OutArgument>  
      </Assign.To>  
    </Assign>  
  </Sequence>  
</Activity>  
```  
  
 <span data-ttu-id="21dc0-121">Pour charger un workflow sérialisé, le <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> méthode est utilisée.</span><span class="sxs-lookup"><span data-stu-id="21dc0-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="21dc0-122">Elle prend la définition de workflow sérialisée et retourne un <xref:System.Activities.DynamicActivity> qui représente la définition de workflow.</span><span class="sxs-lookup"><span data-stu-id="21dc0-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="21dc0-123">Notez que le XAML n'est pas désérialisé tant que <xref:System.Activities.Activity.CacheMetadata%2A> n'est pas appelé sur le corps de <xref:System.Activities.DynamicActivity> pendant le processus de validation.</span><span class="sxs-lookup"><span data-stu-id="21dc0-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="21dc0-124">Si la validation n'est pas appelée explicitement, elle est effectuée lors de l'appel du workflow.</span><span class="sxs-lookup"><span data-stu-id="21dc0-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="21dc0-125">Si la définition de workflow XAML n'est pas valide, une exception <xref:System.Argument> est levée.</span><span class="sxs-lookup"><span data-stu-id="21dc0-125">If the XAML workflow definition is invalid, then an <xref:System.Argument> exception is thrown.</span></span> <span data-ttu-id="21dc0-126">Toutes les exceptions levées à partir de <xref:System.Activities.Activity.CacheMetadata%2A> sont soustraites à l'appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> et doivent être gérées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="21dc0-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="21dc0-127">Dans l'exemple suivant, le workflow sérialisé de l'exemple précédent est chargé et appelé à l'aide de <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="21dc0-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="21dc0-128">Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="21dc0-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="21dc0-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="21dc0-129">**25 + 15**</span></span>  
<span data-ttu-id="21dc0-130">**40**</span><span class="sxs-lookup"><span data-stu-id="21dc0-130">**40**</span></span>    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="21dc0-131">appel de flux de travail avec des arguments d’entrée et de sortie, consultez [à l’aide de WorkflowInvoker et WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) et <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="21dc0-131"> invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="21dc0-132">Si le workflow sérialisé contient des expressions c#, alors un <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> de l’instance avec son <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> propriété la valeur `true` doit être passé en tant que paramètre à <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, sinon un <xref:System.NotSupportedException> sera levée avec un message semblable à la suivant : `Expression Activity type 'CSharpValue`1' requiert une compilation pour pouvoir pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="21dc0-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="21dc0-133">Veuillez vous assurer que le flux de travail a été compilé. »</span><span class="sxs-lookup"><span data-stu-id="21dc0-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="21dc0-134">[Expressions c#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="21dc0-134"> [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="21dc0-135">Une définition de workflow sérialisée peut également être chargée dans un <xref:System.Activities.ActivityBuilder> instance à l’aide de la <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="21dc0-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="21dc0-136">Une fois qu'un workflow sérialisé est chargé dans une instance <xref:System.Activities.ActivityBuilder>, il peut être inspecté et modifié.</span><span class="sxs-lookup"><span data-stu-id="21dc0-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="21dc0-137">Cette possibilité, qui est utile pour les auteurs de concepteurs de workflow personnalisés, fournit un mécanisme permettant d'enregistrer et de recharger des définitions de workflow pendant le processus de conception.</span><span class="sxs-lookup"><span data-stu-id="21dc0-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="21dc0-138">Dans l'exemple suivant, la définition de workflow sérialisée de l'exemple précédent est chargée et ses propriétés sont inspectées.</span><span class="sxs-lookup"><span data-stu-id="21dc0-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
