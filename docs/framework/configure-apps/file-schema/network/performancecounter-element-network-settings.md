---
title: "&lt;performanceCounters&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<performanceCounter> (élément)"
  - "performanceCounter (élément)"
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;performanceCounters&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Active ou désactive les compteurs de performance réseau.  
  
## Syntaxe  
  
```  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Spécifie si les compteurs de performance réseau sont activés.  La valeur par défaut est `false`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
 Les compteurs de performance réseau doivent être activés dans le fichier de configuration à utiliser.  Tous les compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration.  Des compteurs de performance réseau individuels ne peuvent pas être activés ou désactivés.  Pour plus d'informations sur des compteurs de performance réseau spécifiques, consultez [Networking Performance Counters](http://msdn.microsoft.com/fr-fr/d1860235-f643-46ae-846c-ff0ed8b0e3cd).  
  
 La valeur par défaut est que les compteurs de performance réseau sont désactivés.  
  
 La propriété <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut **enabled** de fichiers de configuration applicables.  
  
## Exemple  
 L'exemple de code suivant indique comment configurer <xref:System.Net> et les espaces de noms connexes pour activer des compteurs de performance réseau.  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [Networking Performance Counters](http://msdn.microsoft.com/fr-fr/d1860235-f643-46ae-846c-ff0ed8b0e3cd)