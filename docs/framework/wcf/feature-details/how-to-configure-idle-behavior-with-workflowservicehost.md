---
title: "Procédure : configurer le comportement inactif avec WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ec203ecf1041955c140f3409c090db756e5c34d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="13206-102">Procédure : configurer le comportement inactif avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="13206-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="13206-103">Les workflows deviennent inactifs lorsqu'ils rencontrent un signet qui doit être repris au moyen d'une impulsion externe, par exemple, l'instance de workflow attend qu'un message soit remis à l'aide d'une activité <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="13206-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="13206-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> est un comportement qui vous permet de spécifier le délai entre le moment où une instance du service devient inactive et celui où elle est persistante ou déchargée.</span><span class="sxs-lookup"><span data-stu-id="13206-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="13206-105">Il contient deux propriétés qui permettent de définir ces intervalles.</span><span class="sxs-lookup"><span data-stu-id="13206-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="13206-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> spécifie l'intervalle de temps entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante.</span><span class="sxs-lookup"><span data-stu-id="13206-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="13206-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> spécifie l'intervalle entre le moment où une instance du service de workflow devient inactive et celui où elle est déchargée, c'est-à-dire rendue persistante dans le magasin d'instances et supprimée de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="13206-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="13206-108">Cette rubrique explique comment configurer le comportement <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="13206-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="13206-109">Pour configurer WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="13206-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="13206-110">Ajouter un <`workflowIdle`> élément à la <`behavior`> élément dans le <`serviceBehaviors`> élément, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="13206-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="13206-111">L'attribut `timeToUnload` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où le service de workflow est déchargé.</span><span class="sxs-lookup"><span data-stu-id="13206-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="13206-112">L'attribut `timeToPersist` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante.</span><span class="sxs-lookup"><span data-stu-id="13206-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="13206-113">La valeur par défaut de `timeToUnload` est égale à 1 minute.</span><span class="sxs-lookup"><span data-stu-id="13206-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="13206-114">La valeur par défaut de `timeToPersist` est <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="13206-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="13206-115">Si vous souhaitez conserver les instances inactives en mémoire mais les rendre persistantes pour plus de fiabilité, définissez les valeurs ainsi : `timeToPersist` < `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="13206-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="13206-116">Si vous souhaitez empêcher que les instances inactives soient déchargées, définissez `timeToUnload` sur <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="13206-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="13206-117"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, consultez [extensibilité d’hôte de Service de Workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="13206-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13206-118">L'exemple de configuration précédent utilise la configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="13206-118">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="13206-119">[Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="13206-119"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="13206-120">Pour modifier le comportement de l'inactivité en code</span><span class="sxs-lookup"><span data-stu-id="13206-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="13206-121">L’exemple suivant modifie la temporisation avant la persistance et le déchargement par programmation.</span><span class="sxs-lookup"><span data-stu-id="13206-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="13206-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13206-122">See Also</span></span>  
 [<span data-ttu-id="13206-123">Extensibilité d’hôte de Service de workflow</span><span class="sxs-lookup"><span data-stu-id="13206-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="13206-124">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="13206-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="13206-125">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="13206-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
