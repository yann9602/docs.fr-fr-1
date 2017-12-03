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
ms.openlocfilehash: 9e85f8010528d18133ccd9d98de8479ea0de343d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Pour configurer WorkflowUnhandledExceptionBehavior  
  
1.  Ajouter un <`workflowUnhandledException`> élément dans un <`behavior`> élément au sein d’un <`serviceBehaviors`> élément, à l’aide de la `action` attribut pour spécifier l’action à entreprendre lorsqu’une exception non gérée se produit, comme indiqué dans l’exemple suivant.  
  
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
    >  L'exemple de configuration précédent utilise la configuration simplifiée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     Le `action` attribut de la <`workflowUnhandledException`> élément peut être défini à une des valeurs suivantes :  
  
     **Abandon**  
     Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante (autrement dit, restaure le dernier point persistant).  
  
     **abandonAndSuspend**  
     Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.  
  
     **Annuler**  
     Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances  
  
     **terminate**  
     Termine l'instance en mémoire et la supprime du magasin d'instances.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consultez [extensibilité d’hôte de Service de Workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité d’hôte de Service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)
