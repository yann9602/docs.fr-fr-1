---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a>ActivityTransfer
Événement du transfert de l'activité  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ActivityTransfer ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ActivityTransfer a les propriétés suivantes :  
  
### <a name="activityid"></a>ActivityID  
  
-   Type de données : objet  
    Type d'accès : lecture seule  
  
-   ID d'activité  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Type de données : objet  
    Type d'accès : lecture seule  
  
-   ID d'activité connexe  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel.|
