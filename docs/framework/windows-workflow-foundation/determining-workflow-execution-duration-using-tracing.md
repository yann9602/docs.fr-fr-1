---
title: "Détermination de la durée d'exécution d'un workflow à l'aide du suivi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2687d045db28974e99b2f2b6a3222924a520720
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="85c34-102">Détermination de la durée d'exécution d'un workflow à l'aide du suivi</span><span class="sxs-lookup"><span data-stu-id="85c34-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="85c34-103">Cette rubrique montre comment déterminer le temps nécessaire à l'exécution avec succès d'un workflow auto-hébergé à l'aide du suivi de workflow.</span><span class="sxs-lookup"><span data-stu-id="85c34-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="85c34-104">Pour déterminer la durée d'exécution d'une application de workflow à l'aide du suivi</span><span class="sxs-lookup"><span data-stu-id="85c34-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="85c34-105">Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85c34-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="85c34-106">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="85c34-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="85c34-107">Sous **c#**, sélectionnez le **Workflow** nœud.</span><span class="sxs-lookup"><span data-stu-id="85c34-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="85c34-108">Sélectionnez **Application Console de Workflow** à partir de la liste des modèles.</span><span class="sxs-lookup"><span data-stu-id="85c34-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="85c34-109">Nommez le nouveau projet `WorkflowDurationTracing` et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="85c34-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="85c34-110">Ouvrez le fichier Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="85c34-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="85c34-111">Faites glisser une activité <xref:System.Activities.Statements.Delay> sur l'aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="85c34-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="85c34-112">Affectez la valeur 00:00:10 (dix secondes) à la propriété Duration de l'activité.</span><span class="sxs-lookup"><span data-stu-id="85c34-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="85c34-113">Ouvrez l’Observateur d’événements en cliquant sur **Démarrer**, **exécuter**et en entrant `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="85c34-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="85c34-114">Si vous n’avez pas activé le suivi de workflow, développez **journaux des Applications et Services**, **Microsoft**, **Windows**, **serveur d’applications-Applications** .</span><span class="sxs-lookup"><span data-stu-id="85c34-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="85c34-115">Sélectionnez **vue**, **afficher d’analyse et les journaux de débogage**.</span><span class="sxs-lookup"><span data-stu-id="85c34-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="85c34-116">Avec le bouton droit **déboguer** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="85c34-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="85c34-117">Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="85c34-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="85c34-118">Exécutez l'application de workflow en appuyant sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="85c34-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="85c34-119">Dans l'Observateur d'événements, recherchez un événement récent portant l'ID 1009 et un message semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="85c34-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="85c34-120">Notez l'heure à laquelle le message a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="85c34-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="85c34-121">**Activité parent '', DisplayName : '', InstanceId : '' enfant planifiée activité 'WorkflowDurationTracking.Workflow1', DisplayName : 'Workflow1', InstanceId : '1'.**</span><span class="sxs-lookup"><span data-stu-id="85c34-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="85c34-122">Recherchez un autre événement récent portant l'ID 1001 et un message semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="85c34-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="85c34-123">Soustrayez l'heure du message précédent de la valeur enregistrée dans ce message pour déterminer la durée d'exécution du workflow, qui doit être d'environ dix secondes.</span><span class="sxs-lookup"><span data-stu-id="85c34-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="85c34-124">**WorkflowInstance Id : '1bbac57b-3322-498e-9e27-8833fda3a5bf' est terminé dans l’état fermé.**</span><span class="sxs-lookup"><span data-stu-id="85c34-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c34-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c34-125">See Also</span></span>  
 [<span data-ttu-id="85c34-126">Suivi de workflow</span><span class="sxs-lookup"><span data-stu-id="85c34-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="85c34-127">Analyse de Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="85c34-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="85c34-128">Analyse des Applications avec AppFabric</span><span class="sxs-lookup"><span data-stu-id="85c34-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
