---
title: 4202 - StartSqlCommandExecute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5810a30fa8b797a5a8ed533ea6baca3c85d42c0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="4202---startsqlcommandexecute"></a>4202 - StartSqlCommandExecute
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|4202|  
|Mots clés|WFInstanceStore|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'une commande SQL est exécutée.  
  
## <a name="message"></a>Message  
 Démarrage de l'exécution de la commande SQL : %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|Commande SQL exécutée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
