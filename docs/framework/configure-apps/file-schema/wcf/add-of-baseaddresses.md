---
title: '&lt;add&gt; de &lt;baseAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;add&gt; de &lt;baseAddress&gt;
Représente un élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.  
  
 \<système. ServiceModel >  
\<client >  
\<point de terminaison >  
\<hôte >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`baseAddress`|Chaîne indiquant une adresse de base utilisée par l'hôte de service.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Collection d'éléments `baseAddress`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hébergement d’applications WPF](../../../../../docs/framework/wcf/feature-details/hosting.md)
