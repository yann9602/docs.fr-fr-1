---
title: "&lt;remove&gt;, &#233;l&#233;ment de webRequestModules (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> (élément), webRequestModules"
  - "<webRequestModules>, remove (élément)"
  - "remove (élément), webRequestModules"
  - "webRequestModules, remove (élément)"
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;remove&gt;, &#233;l&#233;ment de webRequestModules (param&#232;tres r&#233;seau)
Supprime un module de demande Web personnalisé de l'application.  
  
## Syntaxe  
  
```  
  
      <remove   
  name = "URI prefix"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`name`|Préfixe URI pour les demandes gérées par ce module de demande Web.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.|  
  
## Notes  
 L'élément `remove` supprime le module de demande Web inscrit pour le préfixe URI spécifié.  
  
 La valeur de l'attribut `prefix` doit correspondre aux premiers caractères d'un URI valide ; par exemple, « http » ou « http:\/\/www.contoso.com ».  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant supprime le module de demande Web pour HTTP existant et inscrit un nouveau module de demande Web personnalisé pour les demandes HTTP sur www.contoso.com.  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix = "http">  
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