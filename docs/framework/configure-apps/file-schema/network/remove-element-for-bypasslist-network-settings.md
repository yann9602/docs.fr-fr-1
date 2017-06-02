---
title: "&lt;remove&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist>, remove (élément)"
  - "bypasslist, remove (élément)"
  - "remove (élément), bypasslist"
  - "remove (élément), bypasslist"
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# &lt;remove&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau)
Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.  
  
## Syntaxe  
  
```  
  
      <remove   
   name = "regular expression"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`name`|Expression régulière décrivant une adresse IP ou un nom DNS.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fournit un jeu d'expressions régulières décrivant les adresses qui n'utilisent pas de proxy.|  
  
## Notes  
 L'élément `remove` supprime des expressions régulières décrivant des adresses IP ou des noms de serveurs DNS dans la liste des adresses qui contournent un serveur proxy.  Les adresses ont été définies précédemment dans le fichier de configuration ou à un niveau supérieur dans la hiérarchie de configuration.  
  
 La valeur de l'attribut `name` doit correspondre à une expression régulière qui décrit un ensemble d'adresses IP ou de noms d'hôtes.  
  
 Pour plus d'informations sur les expressions régulières, consultez .[Expressions régulières du .NET Framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant supprime toute définition précédente relative au domaine adventure\-works.com, puis ajoute le domaine contoso.com à la liste de contournement du proxy.  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove name = "[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)