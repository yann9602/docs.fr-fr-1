---
title: 1124 - InvokeMethodIsStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8db91ad18548ac67a1ad2942fb7f57048e272df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1124---invokemethodisstatic"></a>1124 - InvokeMethodIsStatic
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1124|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler est statique.  
  
## <a name="message"></a>Message  
 InvokeMethod « %1 » - la méthode est statique.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Nom complet de l'activité InvokeMethod.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
