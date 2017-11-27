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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
