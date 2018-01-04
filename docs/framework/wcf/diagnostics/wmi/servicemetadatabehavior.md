---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceMetadataBehavior ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceMetadataBehavior a les propriétés suivantes :  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit l'emplacement vers lequel le service redirige les demandes de métadonnées.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
