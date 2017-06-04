---
title: "&lt;system.web&gt;, &#233;l&#233;ment (Param&#232;tres Web) | Microsoft Docs"
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
  - "<system.Web> (élément)"
  - "ASP.NET (système de configuration)"
  - "fichiers de configuration (ASP.NET)"
  - "system.Web (élément)"
  - "fichier de configuration Web.config (ASP.NET)"
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;system.web&gt;, &#233;l&#233;ment (Param&#232;tres Web)
Contient des informations sur la manière dont la couche d'hébergement ASP.NET gère le comportement au niveau du processus.  
  
## Syntaxe  
  
```  
<system.web>  
</system.web>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<applicationPool\>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Spécifie les paramètres de configuration pour les pools d'applications IIS dans un fichier aspnet.config.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Indique l'élément racine dans chaque fichier de configuration qui est utilisé par le Common Language Runtime et les applications [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## Notes  
 L'élément `system.web` et son élément `applicationPool` enfant ont été ajoutés au [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depuis [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].  Lorsque vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou des versions ultérieures en mode intégré, cette combinaison d'éléments vous permet de configurer la manière dont ASP.NET gère les threads et met en file d'attente des demandes lorsqu'il est hébergé dans un pool d'applications IIS.  Si vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou des versions ultérieures en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
## Exemple  
 L'exemple suivant indique comment configurer le comportement au niveau du processus d'ASP.NET dans le fichier aspnet.config lorsqu'ASP.NET est hébergé dans un pool d'applications IIS.  L'exemple suppose qu'IIS s'exécute en mode intégré et que l'application utilise [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou une version ultérieure.  Ce comportement ne se produit pas dans les versions du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] antérieures à [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].  Les valeurs dans l'exemple sont les valeurs par défaut.  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## Voir aussi  
 [\<applicationPool\>, élément \(Paramètres Web\)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)