---
title: "&lt;security&gt;, &#233;l&#233;ment de &lt;ws2007FederationHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;security&gt;, &#233;l&#233;ment de &lt;ws2007FederationHttpBinding&gt;
Définit les paramètres de sécurité de l'élément [\<ws2007FederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md).  
  
## Syntaxe  
  
```  
  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`mode`|Facultatif.  Spécifie le type de sécurité appliqué.  La valeur par défaut est `Message`.  Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## Attribut Mode  
  
|Valeur|Description|  
|------------|-----------------|  
|None|Le message SOAP n'est pas sécurisé pendant le transfert.|  
|Message|L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.  Par défaut, le corps est chiffré et signé.  Le service doit être configuré à l'aide d'un certificat.  L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.|  
|TransportWithMessageCredential|L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.  Le service doit être configuré à l'aide d'un certificat.  L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Définit les paramètres de sécurité au niveau du message.  Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison de [\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## Voir aussi  
 <xref:System.ServiceModel.WSFederationHttpSecurity>   
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>   
 [Comment : créer une liaison WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)