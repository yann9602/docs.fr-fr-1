---
title: "Activités d'exécution dans WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3386138f01d4865b02ca821a30da68e5d73b64e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-activities-in-wf"></a>Activités d'exécution dans WF
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] offre plusieurs activités fournies par le système pour l'accès aux fonctionnalités de l'exécution du workflow, telles que la persistance et l'arrêt de workflow.  
  
|Activité|Description|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|Demande de façon explicite à ce que le workflow rende son état persistant.|  
|<xref:System.Activities.Statements.TerminateWorkflow>|Arrête l'instance de workflow en cours d'exécution.|  
|<xref:System.Activities.Statements.NoPersistScope>|Activité de conteneur qui empêche la persistance des activités enfants.|
