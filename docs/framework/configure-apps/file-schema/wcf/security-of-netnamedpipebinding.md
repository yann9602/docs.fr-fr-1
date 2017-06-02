---
title: "&lt;security&gt; de &lt;netNamedPipeBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;security&gt; de &lt;netNamedPipeBinding&gt;
Définit les paramètres de sécurité d'une liaison.  
  
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
|mode|Spécifie le type de sécurité appliqué à cette liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   None : la sécurité est désactivée.<br />-   Transport : la sécurité est fournie à l'aide de la sécurité sous\-jacente basée sur le transport.  Il est possible de contrôler le niveau de protection avec ce mode.<br />-   La valeur par défaut est Transport.  Cet attribut est de type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|transport|Définit les paramètres de sécurité pour le transport.  Cet élément est de type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Élément de liaison du [\<netNamedPipeBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).|  
  
## Voir aussi  
 <xref:System.ServiceModel.NetNamedPipeSecurity>   
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)