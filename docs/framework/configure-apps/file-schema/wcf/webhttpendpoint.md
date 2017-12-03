---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee055be8c4d2e53dc22a101529e5521add9b54a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpendpointgt"></a>&lt;webHttpEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard avec une liste fixe [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) automatiquement une liaison qui ajoute le [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportement. Utilisez ce point de terminaison lors de l'écriture d'un service REST.  
  
\<système. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Valeur booléenne qui indique si la sélection automatique du format est activée.<br /><br /> Lorsque la sélection automatique du format est activée, l'infrastructure analyse l'en-tête `Accept` du message de demande et détermine le format de réponse le plus approprié. Si l'en-tête `Accept` ne spécifie pas de format de réponse approprié, l'infrastructure utilise le `Content-Type` du message de demande ou le format de réponse par défaut de l'opération.|  
|defaultOutgoingResponseFormat|Attribut qui spécifie le format de réponse sortant par défaut. Cet attribut est de type <xref:System.ServiceModel.Web.WebMessageFormat>.|  
|helpEnabled|Valeur booléenne qui indique si la page d'aide HTTP est activée pour le point de terminaison.|  
|webEndpointType|Chaîne qui spécifie le type du point de terminaison.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
