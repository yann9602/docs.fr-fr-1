---
title: "&lt;appDomainResourceMonitoring&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c9591789c007466adce107732a7ab777b1de241
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appDomainResourceMonitoring&gt; élément
Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.  
  
 \<configuration>  
\<runtime >  
\<appDomainResourceMonitoring >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime collecte des statistiques pour l’analyse de ressource de domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Les statistiques pour l’analyse de ressource de domaine d’application sont collectées.|  
|`false`|Statistiques pour l’analyse de ressource de domaine d’application ne sont pas collectées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 L’analyse de ressource de domaine d’application est disponible via la classe de domaine d’application managée, l’hébergement [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface et le suivi d’événements pour Windows (ETW). Lorsque l’analyse est activée, les statistiques sont collectées pour tous les domaines d’application dans le processus pour la durée de vie du processus.  
  
 Pour activer l’analyse du code managé, utilisez la <xref:System.AppDomain.MonitoringIsEnabled%2A> propriété.  
  
 Cet élément de configuration est uniquement disponible dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer l’analyse de ressource de domaine d’application.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
