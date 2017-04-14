---
title: "&lt;remove&gt;, &#233;l&#233;ment de connectionManagement (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<connectionManagement>, remove (élément)"
  - "<remove> (élément), connectionManagement"
  - "connectionManagement, remove (élément)"
  - "remove (élément), connectionManagement"
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;remove&gt;, &#233;l&#233;ment de connectionManagement (param&#232;tres r&#233;seau)
Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.  
  
## Syntaxe  
  
```  
  
      <remove   
   name = "server name or IP address"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`address`|Adresse IP ou nom DNS.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à un hôte réseau.|  
  
## Notes  
 L'élément `remove` supprime l'entrée de liste de gestion des connexions pour le serveur spécifié.  
  
 La valeur de l'attribut `address` doit être une adresse IP ou un nom d'hôte valide.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant supprime toute entrée de liste de gestion des connexions relative au serveur www.adventure\-works.com, puis configure une application de sorte qu'elle utilise quatre connexions au serveur www.contoso.com et deux connexions à tous les autres serveurs.  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address = "http://www.adventure-works.com"/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.ServicePoint>   
 <xref:System.Net.ServicePointManager>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)