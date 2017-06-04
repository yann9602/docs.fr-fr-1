---
title: "&lt;security&gt; de &lt;basicHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# &lt;security&gt; de &lt;basicHttpBinding&gt;
Définit toutes les fonctions de sécurité du [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
## Syntaxe  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Facultatif.  Spécifie le type de sécurité qui est utilisé.  La valeur par défaut est `None`.  Cet attribut est de type <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## Attribut Mode  
  
|Valeur|Description|  
|------------|-----------------|  
|None|-   Les messages ne sont pas sécurisés pendant le transfert.|  
|Transport|La sécurité est fournie à l'aide du transport HTTPS.  Les messages SOAP sont sécurisés par HTTPS.  Le service est authentifié auprès du client à l'aide du certificat X.509 du service.  Le client est authentifié à l'aide du ClientCredentialType fourni.  Consultez [\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP.  Par défaut, le corps est chiffré et signé.  Pour cette liaison, le système impose que le certificat de serveur soit fourni au client hors bande.  Le seul `ClientCredentialType` valide pour cette liaison est `Certificate`.|  
|TransportWithMessageCredential|L'intégrité, la confidentialité et l'authentification de serveur sont fournies par la sécurité du transport.  L'authentification du client est fournie au moyen de la sécurité des messages SOAP.  Ce mode est utile lorsque l'utilisateur effectue une authentification à l'aide du nom d'utilisateur\/mot de passe et qu'il existe un déploiement HTTP pour sécuriser le transfert des messages.|  
|TransportCredentialOnly|Ce mode n'assure pas l'intégrité et la confidentialité des messages.  Il fournit l'authentification du client basée sur http.  Ce mode doit être utilisé avec précaution.  Il doit être utilisé dans les environnements où la sécurité de transport est fournie par d'autres moyens \(tels que IPSec\) et où seule l'authentification du client est fournie par l'infrastructure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Définit les paramètres de sécurité de transport pour un service HTTP de base.  Cet élément correspond à <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Définit les paramètres de sécurité de message pour un service HTTP de base.  Cet élément correspond à <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Élément de liaison du [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## Notes  
 Par défaut, le message SOAP n'est pas sécurisé et le client n'est pas authentifié.  Cet élément permet de configurer des paramètres de sécurité supplémentaires pour l'élément `basicHttpBinding`.  
  
## Voir aussi  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)