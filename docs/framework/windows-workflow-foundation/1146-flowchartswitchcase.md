---
title: 1146 - FlowchartSwitchCase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 265cc4693ab7c6c3719936659250e706c972e02d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1146---flowchartswitchcase"></a>1146 - FlowchartSwitchCase
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1146|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique le cas sélectionné dans un commutateur Flowchart.  
  
## <a name="message"></a>Message  
 Flowchart « %1 »/FlowSwitch - Le cas « %2 » a été sélectionné.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Organigramme|xs:string|Nom complet de l'organigramme.|  
|Case|xs:string|Le cas switch sélectionné.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
