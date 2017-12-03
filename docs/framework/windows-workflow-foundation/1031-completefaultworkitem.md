---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1031|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'un FaultWorkItem est terminé.  
  
## <a name="message"></a>Message  
 Un FaultWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ». L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|Nom de type de l'activité d'erreur.|  
|FaultActivityDisplayName|xs:string|Nom complet de l'activité d'erreur.|  
|FaultActivityInstanceId|xs:string|ID d'instance de l'activité d'erreur.|  
|ExceptionActivity|xs:string|Nom de type de l'activité qui a levé l'exception.|  
|ExceptionActivityDisplayName|xs:string|Nom complet de l'activité qui a levé l'exception.|  
|ExceptionActivityInstanceId|xs:string|ID d'instance de l'activité ayant levé l'exception.|  
|Exception|xs:string|Détails de l'exception|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
