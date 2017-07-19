---
title: "Activit&#233;s Gestion des erreurs dans le WF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Activit&#233;s Gestion des erreurs dans le WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] offre plusieurs activités fournies par le système pour implémenter la gestion et la récupération des erreurs.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Exceptions](../../../docs/framework/windows-workflow-foundation//exceptions.md).  
  
## Activités de gestion des erreurs  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Lève de nouveau la dernière exception levée à partir d'une activité `TryCatch`.|  
|<xref:System.Activities.Statements.Throw>|Lève une exception.|  
|<xref:System.Activities.Statements.TryCatch>|Implémente la gestion des exceptions.|