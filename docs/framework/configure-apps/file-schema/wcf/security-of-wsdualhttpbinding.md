---
title: "&lt;security&gt; de &lt;wsDualHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;security&gt; de &lt;wsDualHttpBinding&gt;
Définit toutes les fonctions de sécurité du [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
## Syntaxe  
  
```  
  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|-   Facultatif.  Spécifie le type de sécurité appliqué.  La valeur par défaut est `Message`.  Cet attribut est de type <xref:System.ServiceModel.WSDualHttpSecurityMode>.|  
  
## Mode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|None|La sécurité est désactivée.|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|Définit les paramètres de sécurité au niveau du message.  Cet élément est de type <xref:System.ServiceModel.MessageSecurityOverHttp>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison de [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## Notes  
 Une liaison double expose l'adresse IP du client au service.  Ce client doit utiliser un mode de sécurité qui vérifiera qu'il se connecte uniquement à des services de confiance.  
  
## Voir aussi  
 <xref:System.ServiceModel.WSDualHttpSecurity>   
 <xref:System.ServiceModel.WsDualHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)