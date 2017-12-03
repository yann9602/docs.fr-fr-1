---
title: '&lt;adresses de base&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe66b499eb50a058ed8b6a46769893f6dc5fd6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressesgt"></a>&lt;adresses de base&gt;
Représente une collection d'éléments `baseAddress`, qui sont les adresses de base d'un hôte de service dans un environnement auto-hébergé. Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.  
  
 \<système. ServiceModel >  
\<client >  
\<point de terminaison >  
\<hôte >  
\<baseAddresses >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<hôte >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Élément de configuration qui spécifie des paramètres pour un hôte de service.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hébergement d’applications WPF](../../../../../docs/framework/wcf/feature-details/hosting.md)
