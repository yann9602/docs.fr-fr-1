---
title: "&lt;add&gt;, &#233;l&#233;ment de webRequestModules (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément), webRequestModules"
  - "<webRequestModules>, add (élément)"
  - "add (élément), webRequestModules"
  - "webRequestModules, add (élément)"
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# &lt;add&gt;, &#233;l&#233;ment de webRequestModules (param&#232;tres r&#233;seau)
Ajoute un module de demande Web personnalisé à l'application.  
  
## Syntaxe  
  
```  
  
      <add   
  prefix = "URI prefix"   
  type = "module name, Version, Culture, PublicKeyToken"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`prefix`|Préfixe URI pour les demandes gérées par ce module de demande Web.|  
|`type`|Assembly et nom de classe du module qui implémente ce module de demande Web.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.|  
  
## Notes  
 L'attribut `prefix` définit le préfixe URI qui utilise le module de demande Web spécifié.  Les modules de demande Web sont généralement inscrits de façon à gérer un protocole spécifique, tel que HTTP ou FTP, mais ils peuvent également l'être pour gérer une demande envoyée vers un serveur ou un chemin d'accès sur un serveur spécifiques.  
  
 Le module de demande Web est créé lorsqu'un préfixe URI correspondant est passé à la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName>.  
  
 La valeur de l'attribut `prefix` doit correspondre aux premiers caractères d'un URI valide ; par exemple, « http » ou « http:\/\/www.contoso.com ».  
  
 La valeur pour l'attribut `type` doit comprendre un nom de DLL valide et le nom de classe correspondant, séparés par une virgule.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant inscrit un module de demande Web personnalisé pour HTTP.  Vous devez remplacer les valeurs de Version et de PublicKeyToken par les valeurs correctes pour le module spécifié.  
  
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
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)