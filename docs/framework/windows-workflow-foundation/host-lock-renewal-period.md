---
title: "Période de renouvellement du verrou de l'hôte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7447d11e93cf33e69bc52d2cdec239c1be55bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="host-lock-renewal-period"></a>Période de renouvellement du verrou de l'hôte
Le **Host Lock Renewal Period** propriété du magasin d’instances de Workflow SQL vous permet de spécifier la période durant laquelle l’hôte renouvelle son verrou sur une instance de workflow. Le verrou reste valide pendant la période spécifiée pour la propriété Host Lock Renewal Period + 30 secondes. Si l'hôte ne renouvelle pas le verrou (en d'autres termes, s'il étend le bail) durant cette période, le verrou expire et le fournisseur de persistance déverrouille l'instance. La valeur de cette propriété est de type TimeSpan sous la forme « hh : mm : ». La valeur minimale autorisée est « 00 : 00:01 » (1 seconde). La valeur par défaut de cette propriété est « 00 : 00:30 » (30 secondes).  
  
 Cette propriété est significative dans les scénarios où un hôte du service de workflow échoue avant d'avoir pu déverrouiller une instance de service du workflow qu'il possède. Dans ce scénario, le verrou de l'instance du service de workflow dans la base de données de persistance est supprimé par le fournisseur de persistance après l'expiration du verrou afin qu'un autre hôte du service de workflow qui s'exécute sur le même ordinateur ou sur un autre ordinateur dans une batterie de serveurs puisse acquérir le verrou et charger l'instance du service de workflow en mémoire pour reprendre son exécution à partir de son dernier état persistant.  
  
 Le fait de définir une valeur plus élevée pour cette propriété a pour effet de verrouiller les instances du service de workflow dans la base de données de persistance pendant plus longtemps et par conséquent de retarder la récupération de l'instance à partir du dernier point de persistance. Si vous définissez un intervalle court pour cette propriété, la nouvelle instance de l'hôte du service de workflow récupère rapidement l'instance du service de workflow ayant échoué, mais provoque une augmentation dans la charge de travail pour l'hôte du service de workflow et la base de données SQL Server.  
  
 Le magasin d'instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances dont les verrous sont périmés. Lorsqu'il trouve des instances dont les verrous sont périmés, il place les instances dans la table RunnableInstances afin qu'un hôte de workflow puisse récupérer et exécuter ces instances.
