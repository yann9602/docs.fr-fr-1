---
title: "Utilisation du suivi pour résoudre les problèmes posés par les applications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52a599d9cba2e68fdb74d364dad562d2547ca020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="e44b8-102">Utilisation du suivi pour résoudre les problèmes posés par les applications</span><span class="sxs-lookup"><span data-stu-id="e44b8-102">Using Tracking to Troubleshoot Applications</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="e44b8-103"> vous permet de suivre les informations associées au workflow pour donner des détails concernant l'exécution d'une application de [!INCLUDE[wf2](../../../includes/wf2-md.md)] ou d'un service.</span><span class="sxs-lookup"><span data-stu-id="e44b8-103"> enables you to track workflow-related information to give details into the execution of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] application or service.</span></span> <span data-ttu-id="e44b8-104">Les hôtes de [!INCLUDE[wf2](../../../includes/wf2-md.md)] sont en mesure de capturer des événements du workflow pendant l'exécution d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="e44b8-104">[!INCLUDE[wf2](../../../includes/wf2-md.md)] hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="e44b8-105">Si votre workflow génère des erreurs ou des exceptions, vous pouvez utiliser les détails du suivi [!INCLUDE[wf2](../../../includes/wf2-md.md)] pour résoudre les problèmes liés à son traitement.</span><span class="sxs-lookup"><span data-stu-id="e44b8-105">If your workflow generates faults or exceptions, you can use the [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="e44b8-106">Dépannage d'un WF à l'aide du suivi WF</span><span class="sxs-lookup"><span data-stu-id="e44b8-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="e44b8-107">Pour détecter des erreurs dans le traitement d'une activité [!INCLUDE[wf2](../../../includes/wf2-md.md)], vous pouvez activer le suivi avec un modèle de suivi chargé de rechercher un <xref:System.Activities.Tracking.ActivityStateRecord> dont l'état est Faulted.</span><span class="sxs-lookup"><span data-stu-id="e44b8-107">To detect faults within the processing of a [!INCLUDE[wf2](../../../includes/wf2-md.md)] activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="e44b8-108">La requête correspondante est spécifiée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e44b8-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="e44b8-109">Si une erreur est propagée et gérée dans un gestionnaire d'erreur (tel qu'une activité <xref:System.Activities.Statements.TryCatch>), cette erreur peut être détectée à l'aide d'un <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="e44b8-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="e44b8-110"><xref:System.Activities.Tracking.FaultPropagationRecord> indique l'activité source de l'erreur et le nom du gestionnaire d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e44b8-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="e44b8-111"><xref:System.Activities.Tracking.FaultPropagationRecord> contient des détails sur l'erreur sous la forme d'une pile d'exception. La requête permettant de s'abonner à un <xref:System.Activities.Tracking.FaultPropagationRecord> est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e44b8-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="e44b8-112">Si une erreur n'est pas gérée dans le workflow, cela génère une exception non prise en charge au niveau de l'instance du workflow et l'instance du workflow est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="e44b8-112">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="e44b8-113">Pour comprendre les détails de l'exception non prise en charge, le modèle de suivi doit interroger l'enregistrement de l'instance du workflow dont l'état est `state name="UnhandledException"`, comme spécifié dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e44b8-113">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="e44b8-114">Lorsqu'une instance de workflow rencontre une exception non prise en charge, un objet <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> est émis si le suivi [!INCLUDE[wf2](../../../includes/wf2-md.md)] a été activé.</span><span class="sxs-lookup"><span data-stu-id="e44b8-114">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if [!INCLUDE[wf2](../../../includes/wf2-md.md)] tracking has been enabled.</span></span>  
  
 <span data-ttu-id="e44b8-115">Cet enregistrement de suivi contient les détails de l'erreur sous la forme d'une pile d'exception.</span><span class="sxs-lookup"><span data-stu-id="e44b8-115">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="e44b8-116">Il comprend les détails de la source de l'erreur (par exemple, l'activité) qui a échoué et généré une exception non prise en charge. Pour s'abonner aux les événements d'erreur issus de [!INCLUDE[wf2](../../../includes/wf2-md.md)], activez le suivi en ajoutant un participant de suivi.</span><span class="sxs-lookup"><span data-stu-id="e44b8-116">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a [!INCLUDE[wf2](../../../includes/wf2-md.md)], enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="e44b8-117">Configurez ce participant avec un modèle de suivi qui recherche `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord> et `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="e44b8-117">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="e44b8-118">Si le suivi est activé à l'aide du participant de suivi ETW, les événements d'erreur sont émis sur une session ETW.</span><span class="sxs-lookup"><span data-stu-id="e44b8-118">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="e44b8-119">Les événements peuvent être visualisés à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="e44b8-119">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="e44b8-120">Il se trouve dans le nœud **Applications -> l’Observateur d’événements et journaux des Services -> Microsoft -> Windows -> serveur d’applications-Applications** dans le canal analytique.</span><span class="sxs-lookup"><span data-stu-id="e44b8-120">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44b8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e44b8-121">See Also</span></span>  
 [<span data-ttu-id="e44b8-122">Analyse de Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e44b8-122">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="e44b8-123">Analyse des Applications avec AppFabric</span><span class="sxs-lookup"><span data-stu-id="e44b8-123">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
