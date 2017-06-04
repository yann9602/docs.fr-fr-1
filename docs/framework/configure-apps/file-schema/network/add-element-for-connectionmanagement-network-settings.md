---
title: "&lt;add&gt;, &#233;l&#233;ment de connectionManagement (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément), connectionManagement"
  - "<connectionManagement>, add (élément)"
  - "add (élément), connectionManagement"
  - "connectionManagement, add (élément)"
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;add&gt;, &#233;l&#233;ment de connectionManagement (param&#232;tres r&#233;seau)
Ajoute une adresse IP ou un nom DNS à la liste de gestion des connexions.  
  
## Syntaxe  
  
```  
  
        <add   
   address = "address expression"   
   maxconnection = integer   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`address`|Chaîne décrivant une adresse IP ou un nom DNS.|  
|`maxconnection`|Nombre maximal de connexions à un serveur.  Si aucune valeur n'est indiquée, la valeur par défaut 2 est utilisée.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à un hôte réseau.|  
  
## Notes  
 La valeur de l'attribut `address` doit être un astérisque pour spécifier toutes les connexions, ou une chaîne au format `<schema>://<idn_hostname>[:<port>]`.  
  
 Si l'URI passé à une API HTTP contient des caractères Unicode, le nom est converti en interne à l'aide de <xref:System.Uri.DnsSafeHost%2A> qui peut éventuellement retourner une chaîne Punycode \(le comportement dépend de la configuration IDN actuelle\).  
  
## Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant configure une application qui pourra utiliser quatre connexions au serveur www.contoso.com et deux connexions à tous les autres serveurs.  
  
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