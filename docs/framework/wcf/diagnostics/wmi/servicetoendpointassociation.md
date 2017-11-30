---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mappe un service à un point de terminaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceToEndpointAssociation ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceToEndpointAssociation a les propriétés suivantes :  
  
### <a name="ref"></a>ref  
 Type de données : service  
  
 Type d'accès : lecture seule  
Qualificateurs : clé  
  
 Service associé au point de terminaison.  
  
### <a name="ref"></a>ref  
 Type de données : point de terminaison  
  
 Type d'accès : lecture seule  
Qualificateurs : clé  
  
 Point de terminaison associé au service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
