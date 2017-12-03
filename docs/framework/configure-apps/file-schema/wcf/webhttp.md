---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b5388a680816bca6051525f5130308a3c7c2dc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpgt"></a>&lt;webHttp&gt;
Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration. Ce comportement est utilisé conjointement avec la [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) permet à une liaison standard, le modèle de programmation Web pour un [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.  
  
 \<système. ServiceModel >  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
\<webHttp >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser. La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante. La sélection automatique du format peut être activée par programme ou par configuration.|  
|defaultBodyStyle|Spécifie le style du corps par défaut des messages retournés. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Web.WebMessageBodyStyle> et [mise en forme de HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Spécifie le format de réponse sortante par défaut des messages. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Mise en forme de HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtient ou définit l'indicateur qui spécifie si FaultException est généré lorsqu'une erreur de serveur interne (code d'état HTTP: 500) se produit.|  
|helpEnabled|Obtient ou définit une valeur qui détermine si la page d'aide est activée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie le jeu de comportements du point de terminaison.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Intégration d’AJAX et prise en charge JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
