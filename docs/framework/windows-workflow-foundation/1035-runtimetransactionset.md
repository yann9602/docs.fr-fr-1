---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1035|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'une activité a défini la transaction d'exécution.  
  
## <a name="message"></a>Message  
 La transaction runtime a été définie par l’activité '%1', DisplayName : '%2', InstanceId : '%3'.  L’exécution isolée à l’activité '%4', DisplayName : '%5', InstanceId : '%6'.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|IsolatedActivity|xs:string|Nom de type de l'activité dans laquelle la transaction est isolée.|  
|IsolatedActivityDisplayName|xs:string|Nom complet de l'activité dans laquelle la transaction est isolée.|  
|IsolatedActivityInstanceId|xs:string|ID d'instance de l'activité dans laquelle la transaction est isolée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
