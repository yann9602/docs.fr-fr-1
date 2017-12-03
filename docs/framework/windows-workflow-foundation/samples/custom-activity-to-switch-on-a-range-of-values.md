---
title: "Activité personnalisée pour commuter une plage de valeurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4dcaf023960aab1989493475fe4e5306623adf8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="70f4d-102">Activité personnalisée pour commuter une plage de valeurs</span><span class="sxs-lookup"><span data-stu-id="70f4d-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="70f4d-103">Cet exemple montre comment créer une activité personnalisée qui étend l'utilisation d'un <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="70f4d-104">Une instruction <xref:System.Activities.Statements.Switch%601> classique autorise la commutation basée sur une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="70f4d-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="70f4d-105">Mais dans certains scénarios d'application professionnelle, la commutation d'une activité est basée sur une plage de valeurs.</span><span class="sxs-lookup"><span data-stu-id="70f4d-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="70f4d-106">Par exemple, une activité peut exécuter une action lorsque la valeur de commutation est comprise entre 1 et 5, une autre action lorsque la valeur est comprise entre 6 et 10, et une action par défaut pour toutes les autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="70f4d-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="70f4d-107">Cette activité personnalisée permet exactement ce scénario.</span><span class="sxs-lookup"><span data-stu-id="70f4d-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="70f4d-108">Activité SwitchRange</span><span class="sxs-lookup"><span data-stu-id="70f4d-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="70f4d-109">L'activité `SwitchRange` planifie une activité enfant lorsque la valeur de résultat de son expression est comprise dans la plage de l'un de ses `Cases`.</span><span class="sxs-lookup"><span data-stu-id="70f4d-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="70f4d-110">L'exemple de code suivant est une activité personnalisée qui commute en fonction d'une plage de valeurs.</span><span class="sxs-lookup"><span data-stu-id="70f4d-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="70f4d-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="70f4d-111">Property</span></span>|<span data-ttu-id="70f4d-112">Description</span><span class="sxs-lookup"><span data-stu-id="70f4d-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="70f4d-113">Expression</span><span class="sxs-lookup"><span data-stu-id="70f4d-113">Expression</span></span>|<span data-ttu-id="70f4d-114">Il s'agit de l'expression à évaluer et à comparer par rapport aux plages spécifiées dans la liste Cases.</span><span class="sxs-lookup"><span data-stu-id="70f4d-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="70f4d-115">Le résultat de l'expression est de type T.</span><span class="sxs-lookup"><span data-stu-id="70f4d-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="70f4d-116">Cases</span><span class="sxs-lookup"><span data-stu-id="70f4d-116">Cases</span></span>|<span data-ttu-id="70f4d-117">Chaque cas se compose d'une plage (From et To) et d'une activité (Body).</span><span class="sxs-lookup"><span data-stu-id="70f4d-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="70f4d-118">L'expression est évaluée et comparée par rapport aux plages.</span><span class="sxs-lookup"><span data-stu-id="70f4d-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="70f4d-119">Si le résultat de l'expression est compris dans la plage de l'un des cas, l'activité correspondante est exécutée.</span><span class="sxs-lookup"><span data-stu-id="70f4d-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="70f4d-120">Par défaut</span><span class="sxs-lookup"><span data-stu-id="70f4d-120">Default</span></span>|<span data-ttu-id="70f4d-121">Activité qui est exécutée lorsque aucune correspondance n'est obtenue pour le cas.</span><span class="sxs-lookup"><span data-stu-id="70f4d-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="70f4d-122">Lorsque la valeur définie est `null`, aucune action n'est entreprise.</span><span class="sxs-lookup"><span data-stu-id="70f4d-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="70f4d-123">Classe CaseRange</span><span class="sxs-lookup"><span data-stu-id="70f4d-123">CaseRange Class</span></span>  
 <span data-ttu-id="70f4d-124">La classe `CaseRange` représente une plage dans une activité `SwitchRange`.</span><span class="sxs-lookup"><span data-stu-id="70f4d-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="70f4d-125">Chaque instance de `CaseRange` contient une plage (composée d'un `From` et d'un `To`) et une activité `Body` qui est planifiée si l'expression dans `SwitchRange` est évaluée dans la plage.</span><span class="sxs-lookup"><span data-stu-id="70f4d-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="70f4d-126">L'exemple de code suivant est la définition de la classe `CaseRange`.</span><span class="sxs-lookup"><span data-stu-id="70f4d-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="70f4d-127">Les deux classes `SwitchRange` et `CaseRange`, qui sont définies dans l'exemple, sont des classes génériques pouvant fonctionner avec n'importe quel type qui implémente `IComparable`, comme la classe <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="70f4d-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="70f4d-128">Utilisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="70f4d-128">Sample Usage</span></span>  
 <span data-ttu-id="70f4d-129">L'exemple de code suivant illustre l'utilisation de l'activité `SwitchRange`.</span><span class="sxs-lookup"><span data-stu-id="70f4d-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="70f4d-130">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="70f4d-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="70f4d-131">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution SwitchRange.sln.</span><span class="sxs-lookup"><span data-stu-id="70f4d-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="70f4d-132">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="70f4d-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="70f4d-133">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="70f4d-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70f4d-134">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70f4d-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="70f4d-135">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="70f4d-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="70f4d-136">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="70f4d-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70f4d-137">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="70f4d-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`