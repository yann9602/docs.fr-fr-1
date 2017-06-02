---
title: "&lt;bypasslist&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist> (élément)"
  - "bypasslist (élément)"
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;bypasslist&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Fournit un jeu d'expressions régulières décrivant les adresses qui n'utilisent pas de proxy.  
  
## Syntaxe  
  
```  
  
      <bypasslist>   
</bypasslist>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Ajoute une adresse IP ou un nom DNS à la liste de contournement du proxy.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Efface la liste de contournement du proxy.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Supprime une adresse IP ou un nom DNS de la liste de contournement du proxy.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP \(Hypertext Transfer Protocol\).|  
  
## Notes  
 La liste de contournement du proxy contient des expressions régulières qui décrivent les URI auxquels les instances de <xref:System.Net.WebRequest> peuvent accéder directement, sans passer par le serveur proxy.  
  
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