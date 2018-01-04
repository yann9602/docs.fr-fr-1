---
title: 1037 - RuntimeTransactionComplete
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fb3bd4f9b09541e57d9ef2f7f12fad647b29f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1037---runtimetransactioncomplete"></a>1037 - RuntimeTransactionComplete
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1037|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique que la transaction runtime s'est terminée.  
  
## <a name="message"></a>Message  
 La transaction runtime s'est terminée en état « %1 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|État|xs:string|État de la transaction.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
