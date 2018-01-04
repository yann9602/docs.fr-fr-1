---
title: 1007 - WorkflowApplicationPersisted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ddeb7cc60ec7b7976f8ba6b11ce3cd6a41d51a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1007---workflowapplicationpersisted"></a>1007 - WorkflowApplicationPersisted
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1007|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'une application de workflow est persistante.  
  
## <a name="message"></a>Message  
 ID WorkflowApplication : « %1 » était Persisted.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|ID d'application de flux de travail|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
