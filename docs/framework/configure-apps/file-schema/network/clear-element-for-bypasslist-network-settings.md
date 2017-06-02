---
title: "&lt;clear&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist>, clear (élément)"
  - "<clear> (élément), bypasslist"
  - "bypasslist, clear (élément)"
  - "clear (élément), bypasslist"
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;clear&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau)
Efface la liste de contournement du proxy.  
  
## Syntaxe  
  
```  
  
<clear/>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fournit un jeu d'expressions régulières décrivant les adresses qui n'utilisent pas de proxy.|  
  
## Notes  
 L'élément `clear` efface toutes les entrées dans la liste de contournement.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant efface la liste de contournement du proxy, puis ajoute deux adresses à cette liste.  La première contourne le proxy pour tous les serveurs du domaine contoso.com ; la deuxième contourne le proxy pour tous les serveurs dont l'adresse IP commence par 192.168.  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## Voir aussi  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)