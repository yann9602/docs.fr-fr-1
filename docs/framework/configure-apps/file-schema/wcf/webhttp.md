---
title: "&lt;webHttp&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;webHttp&gt;
Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration.  Si ce comportement est utilisé avec la liaison standard [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md), il active le modèle de programmation Web correspondant à un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## Syntaxe  
  
```  
  
<webHttp />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|automaticFormatSelectionEnabled|Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser.  La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante.  La sélection automatique du format peut être activée par programme ou par configuration.|  
|defaultBodyStyle|Spécifie le style du corps par défaut des messages retournés.  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] Voir <xref:System.ServiceModel.Web.WebMessageBodyStyle> et [Mise en forme HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Spécifie le format de réponse sortante par défaut des messages.  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]Pour plus d'informations, consultez [Mise en forme HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtient ou définit l'indicateur qui spécifie si FaultException est généré lorsqu'une erreur de serveur interne \(code d'état HTTP: 500\) se produit.|  
|helpEnabled|Obtient ou définit une valeur qui détermine si la page d'aide est activée.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie le jeu de comportements du point de terminaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.WebHttpElement>   
 <xref:System.ServiceModel.Description.WebHttpBehavior>   
 [Intégration d'AJAX et prise en charge de JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)   
 [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)