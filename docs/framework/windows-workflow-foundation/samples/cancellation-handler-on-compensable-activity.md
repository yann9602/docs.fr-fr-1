---
title: "Gestionnaire d'annulation sur une activité compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89a5350d61600124e3e5073d6788e4f9042cd70f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="7b1ad-102">Gestionnaire d'annulation sur une activité compensable</span><span class="sxs-lookup"><span data-stu-id="7b1ad-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="7b1ad-103">Cet exemple montre l'utilisation d'un gestionnaire d'annulation sur un <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="7b1ad-104">Cet exemple contient deux scénarios qui illustrent l'utilisation de l'annulation <xref:System.Activities.Statements.CompensableActivity>. Le premier scénario contient une activité compensable racine qui contient trois activités compensables enfants.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="7b1ad-105">Deux activités enfants terminent l'exécution de leurs corps d'activité avec succès.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="7b1ad-106">Lorsque le troisième corps d'activité enfant s'exécute, il rencontre une exception gérée en annulant le traitement de la troisième activité, après quoi l'annulation de l'activité racine est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="7b1ad-107">La logique dans l'activité racine de cet exemple consiste à compenser les deux autres activités enfants terminées précédemment.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="7b1ad-108">Le deuxième scénario illustre l'exécution d'un <xref:System.Activities.Statements.TryCatch> en parallèle avec un <xref:System.Activities.Statements.Delay>, qui finit avant la branche <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="7b1ad-109">La condition d'achèvement a la valeur `true` une fois que la première branche est terminée, ce qui provoque l'annulation de l'autre branche.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b1ad-110">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7b1ad-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7b1ad-111">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez CompensationCancellation.sln.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="7b1ad-112">Générez l'exemple en appuyant sur Ctrl+Maj+B ou sélectionnez Générer la solution dans le menu Générer.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="7b1ad-113">Exécutez l'exemple en appuyant sur F5 ou sélectionnez Démarrer le débogage dans le menu Déboguer.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="7b1ad-114">Vous pouvez également appuyer sur Ctrl+F5 ou sélectionner Exécuter sans débogage dans le menu Déboguer.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b1ad-115">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b1ad-116">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b1ad-117">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7b1ad-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b1ad-118">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7b1ad-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`