---
title: "&lt;add&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> (élément), bypasslist"
  - "<bypasslist>, add (élément)"
  - "add (élément), bypasslist"
  - "bypasslist, add (élément)"
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;add&gt;, &#233;l&#233;ment de bypasslist (param&#232;tres r&#233;seau)
Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.  
  
## Syntaxe  
  
```  
  
      <add   
   address = "regular expression"   
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|**address**|Expression régulière décrivant une adresse IP ou un nom DNS.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fournit un jeu d'expressions régulières décrivant les adresses qui n'utilisent pas de proxy.|  
  
## Notes  
 L'élément `add` ajoute des expressions régulières décrivant des adresses IP ou des noms de serveurs DNS dans la liste des adresses qui contournent un serveur proxy.  
  
 La valeur de l'attribut `address` doit correspondre à une expression régulière qui décrit un ensemble d'adresses IP ou de noms d'hôtes.  
  
 Vous devez être vigilant lorsque vous spécifiez une expression régulière pour cet élément.  L'expression régulière "\[un\-z\]\+\\.contoso\\.com" correspond à tout hôte dans le domaine contoso.com, mais elle correspond également à tout hôte dans le domaine contoso.com.cpandl.com.  Pour indiquer uniquement un hôte dans le domaine contoso.com, utilisez une ancre \("$"\): "\[a\-z\]\+\\.contoso\\.com$".  
  
 Pour plus d'informations sur les expressions régulières, consultez .[Expressions régulières du .NET Framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant ajoute deux adresses à la liste de contournement du proxy.  La première contourne le proxy pour tous les serveurs du domaine contoso.com ; la deuxième contourne le proxy pour tous les serveurs dont l'adresse IP commence par 192.168.  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
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