---
title: "&lt;en-têtes&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5e0a56055df588e9e42c4e1855c352c3f0d1b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltheadersgt"></a>&lt;en-têtes&gt;
Un point de terminaison peut être adressé par un ou plusieurs en-têtes SOAP en plus de son URI de base. Le jeu de scénarios où cette opération est utile est un jeu de scénarios intermédiaires SOAP où un point de terminaison requiert que les clients de ce point de terminaison incluent des en-têtes SOAP destinés à des intermédiaires. Cet élément de configuration peut être utilisé pour définir ces en-têtes d'adresse personnalisés. Les entrées de la collection d'en-têtes de points de terminaison sont des éléments XML définis par l'utilisateur. Chaque élément doit être au format XML adéquat.  
  
 \<système. ServiceModel >  
\<client >  
\<point de terminaison >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Region||  
|Membre||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<point de terminaison >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Configure différents types de points de terminaison.|  
  
## <a name="remarks"></a>Remarques  
 Les en-têtes facultatifs fournissent des informations d'adressage plus détaillées pour identifier ou interagir avec le point de terminaison. Par exemple, les en-tête peuvent indiquer comment traiter un message entrant, où le point de terminaison doit envoyer un message de réponse ou quelle instance d'un service utiliser pour traiter un message entrant d'un utilisateur particulier lorsque plusieurs instances sont disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Points de terminaison : Adresses, liaisons et contrats](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
