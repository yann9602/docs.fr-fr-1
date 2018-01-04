---
title: 2578 - TryCatchExceptionFromCatchOrFinally
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 340f8fa140f44e4a85f9b19259dc0a9f49b9b08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a>2578 - TryCatchExceptionFromCatchOrFinally
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|2578|  
|Mots clés|WFActivities|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'une activité Catch ou Finally a levé une exception.  
  
## <a name="message"></a>Message  
 Une activité Catch ou Finally associée à l'activité TryCatch « %1 » a levé une exception.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
