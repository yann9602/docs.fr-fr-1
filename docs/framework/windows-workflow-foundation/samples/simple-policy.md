---
title: Simple Policy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 884a099c1334b53c904173987d2f1ccfe6dd741a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="simple-policy"></a><span data-ttu-id="9ff5a-102">Simple Policy</span><span class="sxs-lookup"><span data-stu-id="9ff5a-102">Simple Policy</span></span>
<span data-ttu-id="9ff5a-103">Cet exemple indique comment utiliser une activité <xref:System.Workflow.Activities.PolicyActivity> dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="9ff5a-104">Le workflow séquentiel de cet exemple est créé à l'aide d'une activité <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="9ff5a-105">Le workflow définit les champs `orderValue`, `customerType` et `discount` utilisés pour configurer un workflow de remise de produit.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="9ff5a-106">Les règles configurées dans le fichier de règles définissent une valeur de remise basée sur `orderValue` et sur `customerType`.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="9ff5a-107">Les champs `orderValue` et `customerType` sont définis dans la définition de classe `SimplePolicyWorkflow` et peuvent être changés pour modifier le comportement.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="9ff5a-108">La remise obtenue est écrite dans la console dans le gestionnaire d'événements <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> défini dans la classe `SimplePolicyWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="9ff5a-109">Pour générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="9ff5a-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="9ff5a-110">Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ff5a-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ff5a-111">Générez la solution en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9ff5a-112">Exécutez la solution sans débogage en appuyant sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="9ff5a-113">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9ff5a-113">To run the sample</span></span>  
  
-   <span data-ttu-id="9ff5a-114">Dans la fenêtre d'invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier SimplePolicy\bin\debug (ou le dossier SimplePolicy\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ff5a-115">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9ff5a-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9ff5a-116">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="9ff5a-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ff5a-117">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9ff5a-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ff5a-118">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="9ff5a-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="9ff5a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ff5a-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="9ff5a-120">Stratégie avancée</span><span class="sxs-lookup"><span data-stu-id="9ff5a-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
