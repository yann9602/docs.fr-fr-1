---
title: "&lt;webRequestModules&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<webRequestModules> (élément)"
  - "webRequestModules (élément)"
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;webRequestModules&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.  
  
## Syntaxe  
  
```  
  
      <webRequestModules>   
</webRequestModules>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Ajoute un module de demande Web personnalisé à l'application.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Supprime tous les modules de demande Web inscrits de l'application.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Supprime un module de demande Web personnalisé de l'application.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[System.Net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework se connecte au réseau.|  
  
## Notes  
 L'élément `webRequestModules` inscrit les descendants de la classe <xref:System.Net.WebRequest> pour gérer les demandes d'informations envoyées à des hôtes réseau.  Les modules de demande Web doivent implémenter l'interface <xref:System.Net.IWebRequestCreate>.  
  
 Le .NET Framework comprend des modules de demande Web pour les URI commençant par http:\/\/, https:\/\/ et file:\/\/.  Vous ne pouvez substituer les modules par défaut qu'en inscrivant un module personnalisé dans le fichier de configuration.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant inscrit le module HTTP par défaut.  Vous devez remplacer les valeurs de Version et de PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.WebRequest>   
 <xref:System.Net.IWebRequestCreate>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)