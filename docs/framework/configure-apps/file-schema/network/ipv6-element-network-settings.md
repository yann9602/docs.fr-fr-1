---
title: "&lt;ipv6&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ipv6> (élément)"
  - "ipv6 (élément)"
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;ipv6&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Active les réponses de protocole IPv6 \(Internet Protocol version 6\) à partir des membres obsolètes de la classe <xref:System.Net.Dns>.  
  
## Syntaxe  
  
```  
  
      <ipv6  
  enabled="true|false"  
/ipv6>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`enabled`|Spécifie si les membres de la classe <xref:System.Net.Dns> retournent des adresses de protocole IPv6.  La valeur par défaut est `false`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
 Ce paramètre active la prise en charge de IPv6 pour les membres obsolètes de la classe <xref:System.Net.Dns> : <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A> et <xref:System.Net.Dns.Resolve%2A>.  Pour les autres membres de l'espace de noms <xref:System.Net?displayProperty=fullName>, les adresses IPv6 peuvent être retournées si le protocole IPv6 est activé dans le système d'exploitation.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant indique comment activer la prise en charge de IPv6 pour la classe <xref:System.Net.Dns>.  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net?displayProperty=fullName>   
 <xref:System.Net.Dns?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)