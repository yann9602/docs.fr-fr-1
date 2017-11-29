---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|57398|  
|Mots clés|WFServices|  
|Niveau|Avertissement|  
|Canal|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  
 Indique que le système a atteint la limite définie pour la limitation des « MaxConcurrentInstances ».  
  
## <a name="message"></a>Message  
 Le système a atteint la limite définie pour la limitation des 'MaxConcurrentInstances'. La limite a été définie sur %1. La valeur de limitation peut être modifiée en modifiant l'attribut « maxConcurrentInstances » de l'élément serviceThrottle ou en modifiant la propriété « MaxConcurrentInstances » à l'aide du comportement ServiceThrottlingBehavior.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom|xs:string|Nom de l'élément.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
