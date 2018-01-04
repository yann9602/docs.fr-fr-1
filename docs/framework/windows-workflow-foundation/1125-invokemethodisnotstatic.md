---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a>1125 - InvokeMethodIsNotStatic
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1125|  
|Mots clés|WFRuntime|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler n'est pas statique.  
  
## <a name="message"></a>Message  
 InvokeMethod « %1 » - la méthode n'est pas statique.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Nom complet de l'activité InvokeMethod.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
