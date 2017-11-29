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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
