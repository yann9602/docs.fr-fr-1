---
title: "Création avec DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02dc1dfda28aae15889c0239f2913a8240869a76
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="2eb72-102">Création avec DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="2eb72-102">DynamicActivity Creation</span></span>
<span data-ttu-id="2eb72-103">Cet exemple montre deux façons différentes de créer une activité au moment de l'exécution à l'aide de l'activité <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="2eb72-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="2eb72-104">Dans cet exemple, une activité est créée au moment de l'exécution avec un corps qui contient une activité <xref:System.Activities.Statements.Sequence> qui contient les activités <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.Assign%601>.</span><span class="sxs-lookup"><span data-stu-id="2eb72-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="2eb72-105">Une liste d'entrée d'entiers est passée dans l'activité et définie comme une propriété.</span><span class="sxs-lookup"><span data-stu-id="2eb72-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="2eb72-106">L'activité <xref:System.Activities.Statements.ForEach%601> itère ensuite au sein de la liste de valeurs et l'accumule.</span><span class="sxs-lookup"><span data-stu-id="2eb72-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="2eb72-107">Dans l'activité <xref:System.Activities.Statements.Assign%601>, la valeur moyenne est calculée en divisant l'accumulateur par le nombre d'éléments dans la liste et en l'affectant à la moyenne.</span><span class="sxs-lookup"><span data-stu-id="2eb72-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="2eb72-108">L'exemple illustre l'utilisation d'une activité <xref:System.Activities.DynamicActivity> qui transfère des variables comme arguments d'entrée et retourne des valeurs comme arguments de sortie.</span><span class="sxs-lookup"><span data-stu-id="2eb72-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="2eb72-109">L'activité a un argument d'entrée nommé `Numbers` qui est une liste d'entiers.</span><span class="sxs-lookup"><span data-stu-id="2eb72-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="2eb72-110">L'activité <xref:System.Activities.Statements.ForEach%601> itère au sein de la liste de valeurs et l'accumule.</span><span class="sxs-lookup"><span data-stu-id="2eb72-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="2eb72-111">Dans l'activité <xref:System.Activities.Statements.Assign%601>, la valeur moyenne est calculée en divisant l'accumulateur par le nombre d'éléments dans la liste et en l'affectant à la moyenne.</span><span class="sxs-lookup"><span data-stu-id="2eb72-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="2eb72-112">La moyenne est retournée comme un argument de sortie nommé `Average`.</span><span class="sxs-lookup"><span data-stu-id="2eb72-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="2eb72-113">Lorsque l'activité dynamique est créée par programmation, l'entrée et la sortie sont déclarées comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2eb72-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 <span data-ttu-id="2eb72-114">L'exemple de code suivant affiche la définition complète du `DynamicActivity` qui calcule la moyenne des valeurs dans une liste.</span><span class="sxs-lookup"><span data-stu-id="2eb72-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 <span data-ttu-id="2eb72-115">En cas de création en XAML, l'entrée et la sortie sont déclarées comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2eb72-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 <span data-ttu-id="2eb72-116">Les données XAML peuvent être créées visuellement à l'aide du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2eb72-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="2eb72-117">S’il est inclus dans un projet Visual Studio, veillez à définir « Action de génération » à « None » pour l’empêcher d’en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="2eb72-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="2eb72-118">Les données XAML peuvent ensuite être chargées dynamiquement à l'aide de l'appel suivant.</span><span class="sxs-lookup"><span data-stu-id="2eb72-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="2eb72-119">L'instance <xref:System.Activities.DynamicActivity> créée par programmation ou par le biais du chargement d'un workflow XAML peut être utilisée comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2eb72-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="2eb72-120">Notez que « acte » passé à la `WorkflowInvoker.Invoke` est le « acte » <xref:System.Activities.Activity> défini dans le premier exemple de code.</span><span class="sxs-lookup"><span data-stu-id="2eb72-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2eb72-121">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="2eb72-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="2eb72-122">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution DynamicActivityCreation.sln.</span><span class="sxs-lookup"><span data-stu-id="2eb72-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2eb72-123">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="2eb72-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2eb72-124">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="2eb72-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="2eb72-125">Arguments de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="2eb72-125">Command line arguments</span></span>  
 <span data-ttu-id="2eb72-126">Cet exemple accepte des arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2eb72-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="2eb72-127">Les utilisateurs peuvent fournir une liste de nombres pour l'activité afin de calculer leur moyenne.</span><span class="sxs-lookup"><span data-stu-id="2eb72-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="2eb72-128">La liste de nombres à utiliser est passée comme une liste de nombres séparés par un espace.</span><span class="sxs-lookup"><span data-stu-id="2eb72-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="2eb72-129">Par exemple, pour calculer la moyenne de 5, 10 et 32, appelez l'exemple à l'aide de la ligne de commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2eb72-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="2eb72-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="2eb72-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="2eb72-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2eb72-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2eb72-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2eb72-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2eb72-133">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2eb72-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2eb72-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2eb72-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`