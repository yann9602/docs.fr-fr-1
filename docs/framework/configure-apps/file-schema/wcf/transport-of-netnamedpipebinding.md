---
title: "&lt;transport&gt; de &lt;netNamedPipeBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;transport&gt; de &lt;netNamedPipeBinding&gt;
Définit les paramètres de sécurité de transport pour un canal nommé.  
  
## Syntaxe  
  
```  
  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|protectionLevel|Définit le niveau de protection du canal nommé.  La signature des messages atténue le risque de modification par un tiers pendant le transfert.  Le chiffrement garantit la confidentialité des données pendant le transport.  Les valeurs valides sont les suivantes :<br /><br /> -   None : aucune protection.<br />-   Sign : les messages sont signés.<br />-   EncryptAndSign : les messages sont chiffrés et signés.<br /><br /> La valeur par défaut est EncryptAndSign.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Définit les paramètres de sécurité d'une liaison.|  
  
## Voir aussi  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)