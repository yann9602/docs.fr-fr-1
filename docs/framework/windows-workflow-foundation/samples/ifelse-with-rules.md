---
title: IfElse With Rules
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bec818ca5492e9a49a602a4f7baef4b45cb073c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="988f7-102">IfElse With Rules</span><span class="sxs-lookup"><span data-stu-id="988f7-102">IfElse With Rules</span></span>
<span data-ttu-id="988f7-103">Cet exemple illustre l'utilisation d'une condition de règle avec une activité <xref:System.Workflow.Activities.IfElseActivity>.</span><span class="sxs-lookup"><span data-stu-id="988f7-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="988f7-104">L'exemple transmet un paramètre `OrderValue` depuis l'hôte.</span><span class="sxs-lookup"><span data-stu-id="988f7-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="988f7-105">La valeur du paramètre est utilisée dans une condition de règle sur la première branche de l'activité <xref:System.Workflow.Activities.IfElseActivity>.</span><span class="sxs-lookup"><span data-stu-id="988f7-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="988f7-106">Si la valeur est inférieure à 10 000, la première branche s’exécute et le <xref:System.Workflow.Activities.CodeActivity> activité de la première branche imprime **obtenir de l’approbation du Gestionnaire de** à la console.</span><span class="sxs-lookup"><span data-stu-id="988f7-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="988f7-107">Si la valeur est supérieure à 10 000, le <xref:System.Workflow.Activities.CodeActivity> activité dans la deuxième branche s’exécute et imprime **obtenir de l’approbation du vice-président**.</span><span class="sxs-lookup"><span data-stu-id="988f7-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="988f7-108">Pour générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="988f7-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="988f7-109">Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="988f7-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="988f7-110">Générez la solution en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="988f7-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="988f7-111">Exécutez la solution sans débogage en appuyant sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="988f7-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="988f7-112">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="988f7-112">To run the sample</span></span>  
  
-   <span data-ttu-id="988f7-113">Dans la fenêtre Invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier IfElseWithRules\bin\debug (ou le dossier IfElseWithRules\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="988f7-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="988f7-114">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="988f7-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="988f7-115">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="988f7-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="988f7-116">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="988f7-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="988f7-117">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="988f7-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="988f7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="988f7-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
