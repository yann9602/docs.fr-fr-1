---
title: "&lt;windowsStreamSecurity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;windowsStreamSecurity&gt;
Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.  
  
## Syntaxe  
  
```  
  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|protectionLevel|Définit la sécurité au niveau du message.  La signature des messages atténue le risque de modification par un tiers pendant le transfert.  Le chiffrement garantit la confidentialité des données pendant le transport.  Les valeurs valides sont les suivantes :<br /><br /> -   None : aucune protection.<br />-   Sign : les messages sont signés.<br />-   EncryptAndSign : les messages sont signés et chiffrés.<br /><br /> La valeur par défaut est EncryptAndSign.<br /><br /> Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données.  Plus spécifiquement, WCF fournit les mises à niveau de la sécurité.  La configuration de cette sécurité de transport est encapsulée par cet élément de configuration, ainsi que par [\<sslStreamSecurity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), qui peut être configuré et ajouté à une liaison personnalisée.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)