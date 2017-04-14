---
title: "Modes d&#39;authentification SecurityBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# Modes d&#39;authentification SecurityBindingElement
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit plusieurs modes par lesquels les clients et services s'authentifient les uns les autres.Vous pouvez créer des éléments de liaison de sécurité pour ces modes d'authentification à l'aide des méthodes statiques sur la classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou via la configuration.Cette rubrique décrit brièvement les 18 modes d'authentification.  
  
 Pour obtenir un exemple d'utilisation de l'élément pour l'un des modes d'authentification, consultez [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## Programmation de configuration de base  
 La procédure suivante décrit comment définir le mode d'authentification dans un fichier de configuration.  
  
#### Pour définir le mode d'authentification dans la configuration  
  
1.  Ajoutez [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) à l'élément [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md).  
  
2.  Ajoutez un élément enfant [\<liaison\>](../../../../docs/framework/misc/binding.md) à l'élément `<customBinding>`.  
  
3.  Ajoutez un élément `<security>` à l'élément `<binding>`.  
  
4.  Affectez l'une des valeurs décrites ci\- dessous à l'attribut `authenticationMode`.Par exemple, le code suivant affecte `AnonymousForCertificate` au mode.  
  
    ```  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### Pour définir le mode par programme  
  
1.  Indiquez l'un des types de retour suivants : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Appelez la méthode statique appropriée de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.Par exemple, le code suivant appelle la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Utilisez l'élément de liaison pour créer la liaison personnalisée.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## Descriptions des modes  
  
### AnonymousForCertificate  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>.Vous pouvez également affecter `AnonymousForCertificate` à l'attribut `authenticationMode` de l'élément \<`security`\>.  
  
### AnonymousForSslNegotiated  
 Avec ce mode d'authentification, le client est anonyme et le service est authentifié à l'aide d'un certificat X.509 négocié au moment de l'exécution.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> lorsqu'une valeur de `false` est passée pour le premier paramètre.Vous pouvez également affecter `AnonymousForSslNegotiated` à l'attribut `authenticationMode`.  
  
### CertificateOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message.Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A>.Vous pouvez également affecter `CertificateOverTransport` à l'attribut `authenticationMode`.  
  
### IssuedToken  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée.Le service n'est pas authentifié auprès du client, en tant que tel, mais le service d'émission de jeton de sécurité chiffre la clé partagée dans le cadre du jeton émis afin que seul le service puisse déchiffrer la clé.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>.Vous pouvez également affecter `IssuedToken` à l'attribut `authenticationMode`.  
  
### IssuedTokenForCertificate  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée.Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message.Le service s'authentifie auprès du client à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>.Vous pouvez également affecter `IssuedTokenForCertificate` à l'attribut `authenticationMode`.  
  
### IssuedTokenForSslNegotiated  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée.Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message.Le service est authentifié à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>.Vous pouvez également affecter `IssuedTokenForSslnegotiated` à l'attribut `authenticationMode`.  
  
### IssuedTokenOverTransport  
 Avec ce mode d'authentification, le client ne s'authentifie pas au service en tant que tel. Au lieu de cela, il s'authentifie à un service de jeton de sécurité et reçoit un jeton SAML, qu'il présente ensuite au serveur pour prouver sa connaissance d'une clé partagée.Le jeton émis apparaît au niveau de la couche SOAP sous la forme d'un jeton de prise en charge d'endossement ou d'un jeton de porteur ; autrement dit, un jeton qui signe la signature de message.Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>.Vous pouvez également affecter `IssuedTokenOverTransport` à l'attribut `authenticationMode`.  
  
### Kerberos  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.Ce même ticket fournit également l'authentification de serveur.L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>.Vous pouvez également affecter `Kerberos` à l'attribut `authenticationMode`.  
  
> [!NOTE]
>  Pour utiliser ce mode d'authentification, le compte de service doit être associé à un SPN \(Service Principal Name, nom de principal du service\).Pour ce faire, exécutez le service sous les comptes SERVICE RÉSEAU ou SYSTÈME LOCAL.Utilisez également l'outil SetSpn.exe pour créer un SPN pour le compte de service.Dans les deux cas, le client doit utiliser le bon SPN dans l'élément [\<servicePrincipalName\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md), ou utiliser le constructeur <xref:System.ServiceModel.EndpointAddress>.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Lorsque le mode d'authentification `Kerberos` est utilisé, les niveaux d'emprunt d'identité <xref:System.Security.Principal.TokenImpersonationLevel> et <xref:System.Security.Principal.TokenImpersonationLevel> ne sont pas pris en charge.  
  
### KerberosOverTransport  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un ticket Kerberos.Le jeton Kerberos apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message.Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A>.Vous pouvez également affecter `KerberosOverTransport` à l'attribut `authenticationMode`.  
  
> [!NOTE]
>  Pour utiliser ce mode d'authentification, le compte de service doit être associé à un SPN.Pour ce faire, exécutez le service sous les comptes SERVICE RÉSEAU ou SYSTÈME LOCAL.Utilisez également l'outil SetSpn.exe pour créer un SPN pour le compte de service.Dans les deux cas, le client doit utiliser le bon SPN dans l'élément [\<servicePrincipalName\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md), ou utiliser le constructeur <xref:System.ServiceModel.EndpointAddress>.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### MutualCertificate  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message.Le service est également authentifié à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.Vous pouvez également affecter `MutualCertificate` à l'attribut `authenticationMode`.  
  
### MutualCertificateDuplex  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un certificat X.509 qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message.Le service est également authentifié à l'aide d'un certificat X.509.La liaison est un `AsymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A>.Vous pouvez également affecter `MutualCertificateDuplex` à l'attribut `authenticationMode`.  
  
### MutalSslNegotiation  
 Avec ce mode d'authentification, le client et le service s'authentifient à l'aide de certificats X.509.L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> lorsqu'une valeur de `true` est passée pour le premier paramètre.Vous pouvez également affecter `MutualSslNegotiated` à l'attribut `authenticationMode`.  
  
### SecureConversation  
 L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>.Cette méthode prend <xref:System.ServiceModel.Channels.SecurityBindingElement> comme paramètre, qui est utilisé pendant l'initialisation pour établir la session sécurisée.Vous pouvez également affecter `SecureConversation` à l'attribut `authenticationMode`.  
  
 Si aucune liaison de démarrage n'est spécifiée, le mode d'authentification `SspiNegotiated` est utilisé pour le démarrage.  
  
### SspiNegotiation  
 Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM \(NT LanMan\).L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A>.Vous pouvez également affecter `SspiNegotiated` à l'attribut `authenticationMode`.  
  
### SspiNegotiatedOverTransport  
 Avec ce mode d'authentification, un protocole de négociation est utilisé pour effectuer l'authentification du client et du serveur.Le protocole Kerberos est dans la mesure du possible utilisé, sinon c'est NTLM.Le jeton résultant apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge d'endossement ; autrement dit, un jeton qui signe la signature de message.Le service est en outre authentifié au niveau de la couche de transport par un certificat X.509.L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A>.Vous pouvez également affecter `SspiNegotiatedOverTransport` à l'attribut `authenticationMode`.  
  
### UserNameForCertificate  
 Avec ce mode d'authentification, le client s'authentifie auprès du service à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message.Le service s'authentifie auprès du client à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.Vous pouvez également affecter `UserNameForCertificate` à l'attribut `authenticationMode`.  
  
 Pour le mode d'authentification `UserNameForCertificate`, le client et le service doivent tous deux utiliser WS\-Security 1.1.  
  
### UserNameForSslNegotiated  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message.Le service est authentifié à l'aide d'un certificat X.509.L'élément de liaison de sécurité est un `SymmetricSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A>.Vous pouvez également affecter `UserNameForSslNegotiated` à l'attribut `authenticationMode`.  
  
### UserNameOverTransport  
 Avec ce mode d'authentification, le client s'authentifie à l'aide d'un jeton de nom d'utilisateur qui apparaît au niveau de la couche SOAP sous forme d'un jeton de prise en charge signé ; autrement dit, un jeton signé par la signature de message.Le service est authentifié à l'aide d'un certificat X.509 au niveau de la couche de transport.L'élément de liaison de sécurité est un `TransportSecurityBindingElement` retourné par la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A>.Vous pouvez également affecter `UserNameOverTransport` à l'attribut `authenticationMode`.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)