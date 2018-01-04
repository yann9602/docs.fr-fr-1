---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a>4211 - QueuingSqlRetry
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|4211|  
|Mots clés|WFInstanceStore|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique une nouvelle tentative de mise en file d'attente SQL.  
  
## <a name="message"></a>Message  
 Mise en file d'attente d'une tentative SQL avec un retard de %1 millisecondes.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Delay|xs:string|Délai entre les tentatives.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
