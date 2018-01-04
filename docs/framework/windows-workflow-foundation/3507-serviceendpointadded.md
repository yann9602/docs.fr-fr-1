---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f06e6cccd9c4ca2907b86372f609f8c72b5e189
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|3507|  
|Mots clés|WFServices|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Indique qu'un point de terminaison du service a été ajouté.  
  
## <a name="message"></a>Message  
 Un point de terminaison du service a été ajouté pour l'adresse « %1 », la liaison « %2 » et le contrat « %3 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Address|xs:string|Adresse du point de terminaison.|  
|Binding|xs:string|Liaison du point de terminaison.|  
|Contrat|xs:string|Contrat du point de terminaison.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
