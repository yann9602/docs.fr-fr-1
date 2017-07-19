---
title: "&lt;mailSettings&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<mailSettings> (élément)"
  - "mailSettings (élément)"
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;mailSettings&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Configure les options d'envoi des messages.  
  
## Syntaxe  
  
```  
  
      <mailSettings  
  <smtp> … </smtp>  
/mailsettings>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Attribut|Description|  
|--------------|-----------------|  
|[\<smtp\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Configure des options SMTP.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[\<system.Net\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont le .NET Framework se connecte au réseau.|  
  
## Exemple  
 L'exemple de code suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l'aide des informations d'identification réseau par défaut.  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Mail.SmtpClient>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)