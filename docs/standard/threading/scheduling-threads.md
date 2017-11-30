---
title: Planification des threads
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a>Planification des threads
Chaque thread a une priorité de thread qui lui est affectée. Threads créés dans le common language runtime sont initialement affectés la priorité de **ThreadPriority.Normal**. Les threads créés en dehors du runtime conservent la priorité qu’ils avaient avant d’entrer dans l’environnement managé. Vous pouvez obtenir ou définir la priorité de n’importe quel thread avec le **Thread.Priority** propriété.  
  
 Threads sont planifiées pour l’exécution en fonction de leur priorité. Même si les threads s’exécutent dans le runtime, tous les threads sont affectés des tranches de temps processeur par le système d’exploitation. Les détails de l’algorithme de planification utilisé pour déterminer l’ordre dans lequel sont exécutés les threads varie en fonction de chaque système d’exploitation. Certains systèmes d’exploitation, le thread avec la priorité la plus élevée (parmi les threads qui peuvent être exécutées) est toujours planifié à exécuter en premier. Si plusieurs threads de priorité identique sont tous disponibles, le planificateur parcourt les threads possédant cette priorité et attribue à chaque thread une tranche de temps fixe dans lequel exécuter. Tant qu’un thread avec une priorité plus élevée est disponible pour être exécuté, les threads de priorité inférieure n’obtiennent pas à exécuter. Lorsqu’il n’y a aucun exécutables threads à une priorité donnée, le planificateur passe à priorité plus et planifie les threads de l’exécution de cette priorité. Si un thread de priorité supérieure est exécutable, le thread de priorité inférieure est retardé, et le thread de priorité plus élevé est autorisé à s’exécuter de nouveau. Sur tout ce qui, le système d’exploitation peut également ajuster les priorités de thread dynamiquement comme interface utilisateur d’une application est déplacée entre les premier et d’arrière-plan. Autres systèmes d’exploitation peut choisir d’utiliser un autre algorithme de planification.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Threading managé et non managé dans Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
