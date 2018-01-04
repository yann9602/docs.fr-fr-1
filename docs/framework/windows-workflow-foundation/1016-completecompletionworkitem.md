---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1016|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'un CompletionWorkItem est terminé.  
  
## <a name="message"></a>Message  
 Un CompletionWorkItem est achevé pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ». Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Nom de type de l'activité parente.|  
|ParentDisplayName|xs:string|Nom complet de l'activité parente.|  
|ParentInstanceId|xs:string|ID d'instance de l'activité parente.|  
|CompletedActivity|xs:string|Nom de type de l'activité achevée.|  
|CompletedActivityDisplayName|xs:string|Nom complet de l'activité achevée.|  
|CompletedActivityInstanceId|xs:string|ID d'instance de l'activité achevée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
