---
title: "Proc&#233;dure&#160;: configurer le comportement des exceptions non g&#233;r&#233;es du workflow avec WorkflowServiceHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Proc&#233;dure&#160;: configurer le comportement des exceptions non g&#233;r&#233;es du workflow avec WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>.Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.  
  
### Pour configurer WorkflowUnhandledExceptionBehavior  
  
1.  Ajoutez un élément \<`workflowUnhandledException`\> dans un élément \<`behavior`\> qui se trouve lui\-même dans un élément \<`serviceBehaviors`\>, en utilisant l'attribut `action` pour spécifier l'action à entreprendre lorsqu'une exception non gérée se produit, comme indiqué dans l'exemple suivant.  
  
    ```  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
    > [!NOTE]
    >  L'exemple de configuration précédent utilise la configuration simplifiée.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
  
    ```  
  
     L'attribut `action` de l'élément \<`workflowUnhandledException`\> peut être défini avec l'une des valeurs suivantes :  
  
     **abandon**  
     Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante \(autrement dit, restaure le dernier point persistant\).  
  
     **abandonAndSuspend**  
     Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.  
  
     **cancel**  
     Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances  
  
     **terminate**  
     Termine l'instance en mémoire et la supprime du magasin d'instances.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consultez [Extensibilité de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## Voir aussi  
 [Extensibilité de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)   
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)