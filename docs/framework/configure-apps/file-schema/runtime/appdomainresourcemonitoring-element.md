---
title: "&lt;appDomainResourceMonitoring&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<appDomainResourceMonitoring> (élément)"
  - "appDomainResourceMonitoring (élément)"
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;appDomainResourceMonitoring&gt;, &#233;l&#233;ment
Indique au runtime de collecter des statistiques sur tous les domaines d'application du processus pendant la durée de vie du processus.  
  
## Syntaxe  
  
```  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime collecte des statistiques pour l'analyse de ressource de domaine d'application.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`true`|Les statistiques pour l'analyse de ressource de domaine d'application sont collectées.|  
|`false`|Les statistiques pour l'analyse de ressource de domaine d'application ne sont pas collectées.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 L'analyse de ressource de domaine d'application est disponible via la classe de domaine d'application managée, l'interface [ICLRAppDomainResourceMonitor](../../../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) d'hébergement et le traçage d'événements pour Windows \(ETW\).  Lorsque l'analyse est activée, les statistiques sont collectées pour tous les domaines d'application dans le processus pendant la durée de vie de celui\-ci.  
  
 Pour activer l'analyse à partir du code managé, utilisez la propriété <xref:System.AppDomain.MonitoringIsEnabled%2A>.  
  
 Cet élément de configuration est disponible uniquement dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et versions ultérieures.  
  
## Exemple  
 L'exemple suivant indique comment activer l'analyse de ressource de domaine d'application.  
  
```  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)