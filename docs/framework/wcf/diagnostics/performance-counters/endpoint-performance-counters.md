---
title: Compteurs de performance de point de terminaison
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc5fa1b3600489cb2d5f31c263019ae5006edf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-performance-counters"></a>Compteurs de performance de point de terminaison
Les compteurs de performance de point de terminaison capturent des données qui révèlent comment un point de terminaison accepte des messages. Ils se trouvent sous l'objet de performance `ServiceModelEndpoint 4.0.0.0` dans l'affichage de l'analyseur de performances. Les instances sont nommées à l’aide du modèle suivant :  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Les données sont semblables à celles recueillies pour des opérations individuelles, mais sont regroupées uniquement sur l'ensemble du point de terminaison.  
  
> [!CAUTION]
>  La longueur du nom d'une instance de compteur de performance est limitée. Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.  
  
## <a name="see-also"></a>Voir aussi  
 [Compteurs de performance](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
