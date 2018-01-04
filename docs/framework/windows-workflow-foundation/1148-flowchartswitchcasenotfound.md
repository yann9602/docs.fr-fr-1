---
title: 1148 - FlowchartSwitchCaseNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0735351f0f5fb830b889d012fd91e3cc99eb255f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1148---flowchartswitchcasenotfound"></a>1148 - FlowchartSwitchCaseNotFound
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1148|  
|Mots clés|WFActivities|  
|Niveau|Information|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'une correspondance de cas ou un cas par défaut est introuvable dans un organigramme. L'exécution de Flowchart va se terminer.  
  
## <a name="message"></a>Message  
 Flowchart « %1 »/FlowSwitch - impossible de trouver l'activité Case ou un cas par défaut correspondant au résultat de l'expression. L'exécution de Flowchart va se terminer.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Organigramme|xs:string|Nom complet de l'organigramme.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
