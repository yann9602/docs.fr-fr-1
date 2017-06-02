---
title: "&lt;module&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#module"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<module> (élément)"
  - "module (élément)"
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;module&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Ajoute un nouveau module proxy à l'application.  
  
## Syntaxe  
  
```  
  
      <module   
   type = "name", System, Version="version number", Culture="culture", PublicKeyToken="token" "   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`type`|Nom et spécifications du module qui implémente le proxy.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP \(Hypertext Transfer Protocol\).|  
  
## Notes  
 L'élément `module` inscrit les classes proxy qui implémentent l'interface <xref:System.Net.IWebProxy>.  Une fois la classe proxy inscrite, `module` peut être utilisé pour demander des informations via le proxy pris en charge.  
  
 La valeur de l'attribut `type` doit correspondre au nom d'une bibliothèque de liens dynamiques \(DLL\) valide et au nom de classe du module.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant inscrit une classe proxy personnalisée.  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type = "Test.CustomWebProxy, System, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.IWebProxy?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)