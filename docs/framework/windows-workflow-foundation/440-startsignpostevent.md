---
title: 440 - StartSignpostEvent1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b7772bcd8d637b14e3f91feceaccc9f045f390c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="440---startsignpostevent1"></a>440 - StartSignpostEvent1
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|440|  
|Mots clés|Résolution des problèmes|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Dans le suivi des activités, indique qu'un message a commencé à traverser une limite d'activité lors d'une opération d'envoi ou de réception.  
  
## <a name="message"></a>Message  
 Limite d'activité.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ExtendedData|`xs:string`|Nom de l'activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
