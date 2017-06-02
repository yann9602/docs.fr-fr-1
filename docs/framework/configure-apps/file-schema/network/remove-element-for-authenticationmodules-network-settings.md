---
title: "&lt;remove&gt;, &#233;l&#233;ment d&#39;authenticationModules (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<authenticationModules>, remove (élément)"
  - "<remove> (élément), authenticationModules"
  - "authenticationModules, remove (élément)"
  - "remove (élément), authenticationModules"
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;remove&gt;, &#233;l&#233;ment d&#39;authenticationModules (param&#232;tres r&#233;seau)
Supprime un module d'authentification de l'application.  
  
## Syntaxe  
  
```  
  
      <remove   
   name = "authentication module name"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|**nom**|Nom du module d'authentification à supprimer.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Spécifie les modules qui servent à authentifier les demandes réseau.|  
  
## Notes  
 L'élément `remove` supprime les modules d'authentification qui ont été définis précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie des fichiers de configuration.  
  
 La valeur de l'attribut `name` doit être un nom de classe valide.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant supprime un module d'authentification.  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove name = "System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)