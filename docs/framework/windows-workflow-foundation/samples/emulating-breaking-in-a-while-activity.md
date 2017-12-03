---
title: "Émulation de l'interruption dans une activité While"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d2d1a0686b96d74bc39a654ee5c9b6f0972a12b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="b5316-102">Émulation de l'interruption dans une activité While</span><span class="sxs-lookup"><span data-stu-id="b5316-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="b5316-103">Cet exemple montre comment interrompre le mécanisme d'exécution en boucle des activités suivantes : <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While> et <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b5316-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="b5316-104">Cela est utile parce que [!INCLUDE[wf](../../../../includes/wf-md.md)] n'inclut aucune activité pour interrompre l'exécution de ces boucles.</span><span class="sxs-lookup"><span data-stu-id="b5316-104">This is useful because [!INCLUDE[wf](../../../../includes/wf-md.md)] does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="b5316-105">Scénario</span><span class="sxs-lookup"><span data-stu-id="b5316-105">Scenario</span></span>  
 <span data-ttu-id="b5316-106">L'exemple recherche le premier fournisseur fiable dans une liste de fournisseurs (instances de la classe `Vendor`).</span><span class="sxs-lookup"><span data-stu-id="b5316-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="b5316-107">Chaque fournisseur a un `ID`, un `Name` et une valeur de fiabilité numérique qui détermine à quel point le fournisseur est digne de confiance.</span><span class="sxs-lookup"><span data-stu-id="b5316-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="b5316-108">L'exemple crée une activité personnalisée appelée `FindReliableVendor` qui reçoit deux paramètres d'entrée (une liste de fournisseurs et une valeur de fiabilité minimale) et retourne le premier fournisseur de la liste qui correspond aux critères fournis.</span><span class="sxs-lookup"><span data-stu-id="b5316-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="b5316-109">Interruption d'une boucle</span><span class="sxs-lookup"><span data-stu-id="b5316-109">Breaking a Loop</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="b5316-110"> n'inclut aucune activité pour interrompre une boucle.</span><span class="sxs-lookup"><span data-stu-id="b5316-110"> does not include an activity to break a loop.</span></span> <span data-ttu-id="b5316-111">L'exemple de code parvient à interrompre une boucle à l'aide d'une activité <xref:System.Activities.Statements.If> et de plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="b5316-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="b5316-112">Dans l'exemple, l'activité <xref:System.Activities.Statements.While> est interrompue une fois qu'une valeur autre que `reliableVendor` a été affectée à la variable `null`.</span><span class="sxs-lookup"><span data-stu-id="b5316-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="b5316-113">L'exemple de code suivant montre comment l'exemple interrompt une boucle while.</span><span class="sxs-lookup"><span data-stu-id="b5316-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b5316-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="b5316-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="b5316-115">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution EmulatingBreakInWhile.sln.</span><span class="sxs-lookup"><span data-stu-id="b5316-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b5316-116">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="b5316-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b5316-117">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="b5316-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5316-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5316-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5316-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b5316-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5316-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b5316-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5316-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b5316-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`