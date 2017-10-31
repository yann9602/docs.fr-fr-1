---
title: "&lt;smtp&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<smtp> (élément)"
  - "smtp (élément)"
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;smtp&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Configure le format de la livraison, la méthode de livraison et l'adresse d'origine pour l'envoi de messages électroniques.  
  
## Syntaxe  
  
```  
  
      <smtp  
  deliveryFormat="format"   
  deliveryMethod="method"   
  from="from address"   
  <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
  <network> … </network>  
/smtp>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`deliveryFormat`|Spécifie le format de remise des courriers électroniques sortants.  Les valeurs acceptables sont SevenBit et International.|  
|`deliveryMethod`|Spécifie la méthode d'acheminement des messages électroniques.  Les valeurs acceptables sont network, pickupDirectoryFromIis et SpecifiedPickupDirectory.|  
|`from`|Spécifie l'adresse d'origine des messages électroniques sortants.|  
  
### Éléments enfants  
  
|Attribut|Description|  
|--------------|-----------------|  
|`specifiedPickupDirectory`|Configure le répertoire local pour un serveur SMTP \(Simple Mail Transport Protocol\).|  
|`network`|Configure les options réseau pour un serveur SMTP externe.|  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[\<mailSettings\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Configure les options d'envoi des messages.|  
  
## Exemple  
 L'exemple de code suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l'aide des informations d'identification réseau par défaut.  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpDeliveryFormat>   
 <xref:System.Net.Mail.SmtpDeliveryMethod>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
