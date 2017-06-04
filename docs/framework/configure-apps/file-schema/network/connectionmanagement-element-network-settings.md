---
title: "&lt;connectionManagement&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<connectionManagement> (élément)"
  - "connectionManagement (élément)"
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;connectionManagement&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Spécifie le nombre maximal de connexions à un hôte réseau.  
  
## Syntaxe  
  
```  
  
      <connectionManagement>   
</connectionManagement>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|Efface la liste de gestion des connexions.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|Supprime une adresse IP ou un nom DNS de la liste de gestion des connexions.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework se connecte au réseau.|  
  
## Notes  
 L'élément `connectionManagement` définit le nombre maximal de connexions à un serveur ou à un groupe de serveurs.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant configure une application de sorte qu'elle utilise quatre connexions au serveur www.contoso.com et deux connexions à tous les autres serveurs.  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
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