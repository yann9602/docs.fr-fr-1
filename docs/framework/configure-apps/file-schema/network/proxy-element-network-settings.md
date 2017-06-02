---
title: "&lt;proxy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<proxy> (élément)"
  - "proxy (élément)"
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;proxy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Définit un serveur proxy.  
  
## Syntaxe  
  
```  
  
      <proxy   
  autoDetect="true|false|unspecified"    
  bypassonlocal="true|false|unspecified"   
  proxyaddress="uriString"  
  scriptLocation="uriString"   
  usesystemdefault="true|false|unspecified "   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`autoDetect`|Spécifie si le proxy est détecté automatiquement.  La valeur par défaut est `unspecified`.|  
|`bypassonlocal`|Spécifie si le proxy est contourné pour les ressources locales.  Les ressources locales incluent le serveur local \(http:\/\/localhost, http:\/\/loopback ou http:\/\/127.0.0.1\) et un URI sans point \(http:\/\/webserver\).  La valeur par défaut est `unspecified`.|  
|`proxyaddress`|Spécifie l'URI de proxy à utiliser.|  
|`scriptLocation`|Spécifie l'emplacement du script de configuration.|  
|`usesystemdefault`|Spécifie s'il faut utiliser des paramètres de proxy Internet Explorer.  Si sa valeur est `true`, les attributs suivants substitueront les paramètres de proxy Internet Explorer.  La valeur par défaut est `unspecified`.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP \(Hypertext Transfer Protocol\).|  
  
## Valeur texte  
  
## Notes  
 L'élément `proxy` définit un serveur proxy pour une application.  Si cet élément est absent du fichier de configuration, le .NET Framework utilise les paramètres de proxy dans Internet Explorer.  
  
 La valeur de l'attribut `proxyaddress` doit être un identificateur URI \(Uniform Resource Indicator\) correct.  
  
 L'attribut `scriptLocation` fait référence à la détection automatique des scripts de configuration du proxy.  La classe <xref:System.Net.WebProxy> tente de localiser un script de configuration \(généralement appelé Wpad.dat\) lorsque l'option **Utiliser un script de configuration automatique** est sélectionnée dans Internet Explorer.  
  
 Utilisez l'attribut `usesystemdefault` pour les applications .NET Framework version 1.1 qui effectuent une migration vers la version 2.0.  
  
 Une exception est levée si l'attribut `proxyaddress` spécifie un proxy par défaut non valide.  La propriété <xref:System.Exception.InnerException%2A> de l'exception doit contenir plus d'informations à propos de la cause première de l'erreur.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l'adresse proxy et contourne le proxy pour l'accès local.  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)