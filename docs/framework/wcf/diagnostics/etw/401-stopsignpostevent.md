---
title: 401 - StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30e796dec45035e6b68659400ebbae1357137b27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="401--stopsignpostevent"></a>401 - StopSignPostEvent
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|401|  
|Mots clés|Résolution des problèmes|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Cet événement marque la fin d'une activité de bout en bout. Il contient le nom de l'activité.  
  
## <a name="message"></a>Message  
 Limite d'activité.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Données étendues|`xs:string`|Nom de l'activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
