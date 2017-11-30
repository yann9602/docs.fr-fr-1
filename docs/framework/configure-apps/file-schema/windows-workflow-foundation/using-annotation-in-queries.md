---
title: "Utilisation de l'annotation dans les requêtes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8713d84af96fa69df5ace33d76ec21560dab2c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="f333c-102">Utilisation de l'annotation dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="f333c-102">Using Annotation in Queries</span></span>
<span data-ttu-id="f333c-103">Grâce aux annotations, vous pouvez baliser arbitrairement des enregistrements de suivi avec une valeur configurable après la génération.</span><span class="sxs-lookup"><span data-stu-id="f333c-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="f333c-104">Par exemple, vous pouvez baliser des plusieurs enregistrements de suivi parmi plusieurs flux de travail en utilisant « Mail Server » == « Mail Server1 ».</span><span class="sxs-lookup"><span data-stu-id="f333c-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="f333c-105">Lors de l’interrogation ultérieure d’enregistrements de suivi, cela facilite la recherche de tous les enregistrements ayant cette étiquette.</span><span class="sxs-lookup"><span data-stu-id="f333c-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="f333c-106">Ajout d'annotations</span><span class="sxs-lookup"><span data-stu-id="f333c-106">Adding Annotations</span></span>  
 <span data-ttu-id="f333c-107">Une annotation peut être ajoutée à une requête de suivi tel qu'indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f333c-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
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
>  <span data-ttu-id="f333c-108">Ces éléments de requête de suivi peuvent être utilisés pour créer un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="f333c-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="f333c-109">Un modèle de suivi peut être créé dans la configuration ou à l'aide du code.</span><span class="sxs-lookup"><span data-stu-id="f333c-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f333c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f333c-110">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="f333c-111">\<participants ></span><span class="sxs-lookup"><span data-stu-id="f333c-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [<span data-ttu-id="f333c-112">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="f333c-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f333c-113">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="f333c-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
