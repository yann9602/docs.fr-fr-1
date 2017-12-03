---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe WSAT_TraceRecord ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe WSAT_TraceRecord a les propriétés suivantes :  
  
### <a name="activityid"></a>ActivityID  
 Type de données : objet  
Type d'accès : lecture seule  
  
 ID d'activité de l'enregistrement de suivi.  
  
### <a name="eventid"></a>EventID  
 Type de données : sint32  
Type d'accès : lecture seule  
  
 ID d'événement de l'enregistrement de suivi.  
  
### <a name="tracerecord"></a>TraceRecord  
 Type de données : chaîne  
Type d'accès : lecture seule  
  
 Enregistrement de suivi  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
