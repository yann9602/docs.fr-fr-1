---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|3508|  
|Mots clés|WFServices|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.  
  
## <a name="message"></a>Message  
 TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable. TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|Nom du modèle de suivi.|  
|ActivityDefinitionId|xs:string|ID de définition d'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
