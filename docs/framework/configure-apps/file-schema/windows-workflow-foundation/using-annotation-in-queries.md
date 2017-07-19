---
title: "Utilisation de l&#39;annotation dans les requ&#234;tes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Utilisation de l&#39;annotation dans les requ&#234;tes
Grâce aux annotations, vous pouvez baliser arbitrairement des enregistrements de suivi avec une valeur configurable après la génération.  Par exemple, vous pouvez baliser plusieurs enregistrements de suivi parmi plusieurs flux de travail en utilisant “Mail Server” \=\= “Mail Server1”.  Lors de l'interrogation ultérieure d'enregistrements de suivi, cela facilite la recherche de tous les enregistrements ayant cette balise.  
  
## Ajout d'annotations  
 Une annotation peut être ajoutée à une requête de suivi tel qu'indiqué dans l'exemple suivant.  
  
```  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
  
```  
  
> [!NOTE]
>  Ces éléments de requête de suivi peuvent être utilisés pour créer un modèle de suivi.  Un modèle de suivi peut être créé dans la configuration ou à l'aide du code.  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>   
 <xref:System.Activities.Tracking.TrackingProfile>   
 [\<participants\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Modèles de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)