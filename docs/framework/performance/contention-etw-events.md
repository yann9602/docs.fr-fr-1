---
title: "Événements ETW de conflit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a>Événements ETW de conflit
Les événements de conflit sont déclenchés chaque fois qu’il existe un conflit sur les verrous <xref:System.Threading.Monitor?displayProperty=nameWithType> ou les verrous natifs utilisés par le runtime. Le conflit se produit quand un thread attend un verrou alors qu’un autre thread possède ce verrou.  
  
 Le tableau suivant montre le mot clé sous lequel les événements de conflit sont déclenchés, ainsi que le niveau des événements. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|Informatif (4)|  
  
 Le tableau suivant affiche des informations sur les événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|Le conflit démarre. Cet événement n’inclut pas le temps qui s’écoule avant qu’un thread ne commence à attendre l’acquisition d’un verrou. Il est déclenché uniquement quand l’attente commence.|  
|`ContentionStop`|81|Le conflit se termine.|  
  
 Le tableau suivant affiche des données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Indicateurs|win:UInt8|0 pour managé ; 1 pour natif.|  
|ClrInstanceID|win:UInt16|ID unique de l’instance de CLR.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
