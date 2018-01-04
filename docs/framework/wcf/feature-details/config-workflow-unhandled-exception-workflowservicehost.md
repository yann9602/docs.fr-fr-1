---
title: "Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b0aa73a1fa96623469e8e3a140e501e7b7a0cfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="79552-102">Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="79552-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="79552-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="79552-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="79552-104">Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="79552-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="79552-105">Pour configurer WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="79552-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="79552-106">Ajouter un <`workflowUnhandledException`> élément dans un <`behavior`> élément au sein d’un <`serviceBehaviors`> élément, à l’aide de la `action` attribut pour spécifier l’action à entreprendre lorsqu’une exception non gérée se produit, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="79552-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="79552-107">L'exemple de configuration précédent utilise la configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="79552-107">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="79552-108">[Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="79552-108"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="79552-109">Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="79552-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="79552-110">Le `action` attribut de la <`workflowUnhandledException`> élément peut être défini à une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="79552-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="79552-111">**Abandon**</span><span class="sxs-lookup"><span data-stu-id="79552-111">**abandon**</span></span>  
     <span data-ttu-id="79552-112">Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante (autrement dit, restaure le dernier point persistant).</span><span class="sxs-lookup"><span data-stu-id="79552-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="79552-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="79552-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="79552-114">Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.</span><span class="sxs-lookup"><span data-stu-id="79552-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="79552-115">**Annuler**</span><span class="sxs-lookup"><span data-stu-id="79552-115">**cancel**</span></span>  
     <span data-ttu-id="79552-116">Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances</span><span class="sxs-lookup"><span data-stu-id="79552-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="79552-117">**terminate**</span><span class="sxs-lookup"><span data-stu-id="79552-117">**terminate**</span></span>  
     <span data-ttu-id="79552-118">Termine l'instance en mémoire et la supprime du magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="79552-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79552-119"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consultez [extensibilité d’hôte de Service de Workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="79552-119"> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79552-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79552-120">See Also</span></span>  
 [<span data-ttu-id="79552-121">Extensibilité de l’hôte du service de workflow</span><span class="sxs-lookup"><span data-stu-id="79552-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="79552-122">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="79552-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
