---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceDebugBehavior ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceDebugBehavior possède les propriétés suivantes :  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie s'il convient d'inclure des informations d'exception gérées dans les détails des fautes SOAP renvoyées aux clients à des fins de débogage.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
