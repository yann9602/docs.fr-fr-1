---
title: '&lt;add&gt; de &lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd487238ebe327a5f89b737fdf764d94f955a411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a>&lt;add&gt; de &lt;defaultPorts&gt;
Point de terminaison de communication par défaut écouté par l'application cliente.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|port|Entier qui spécifie le numéro de port de communication par défaut.|  
|scheme|Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
