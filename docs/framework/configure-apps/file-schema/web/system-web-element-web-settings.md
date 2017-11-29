---
title: "&lt;System.Web&gt; élément (paramètres Web)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 44a978eae9ae85e1ba12f117288a3c9ce4db75b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System.Web&gt; élément (paramètres Web)
Contient des informations sur la façon dont la couche d’hébergement ASP.NET gère le comportement au niveau du processus.  
  
 \<configuration>  
\<System.Web >, élément (paramètres Web)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Spécifie les paramètres de configuration de pools d’applications IIS dans un fichier aspnet.config.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Spécifie l’élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] .|  
  
## <a name="remarks"></a>Remarques  
 Le `system.web` élément et son enfant `applicationPool` élément ont été ajoutés à la [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] de [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Lorsque vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versions ultérieures en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les threads et comment il file d’attente les demandes lorsqu’il est hébergé dans un pool d’applications IIS. Si vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer le comportement au niveau du processus ASP.NET dans le fichier aspnet.config lorsqu’il est hébergé dans un pool d’applications IIS. L’exemple suppose qu’IIS est en cours d’exécution dans intégré mode et que l’application est à l’aide de la [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou une version ultérieure. Ce comportement ne se produit pas dans les versions de la [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] antérieure à la [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Les valeurs dans l’exemple sont les valeurs par défaut.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi  
 [\<applicationPool >, élément (paramètres Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
