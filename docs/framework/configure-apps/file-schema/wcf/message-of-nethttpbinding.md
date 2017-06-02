---
title: "&lt;message&gt; of &lt;netHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;message&gt; of &lt;netHttpBinding&gt;
Définit les paramètres de sécurité au niveau du message de [\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
## Syntaxe  
  
```  
  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|algorithmSuite|Définit les algorithmes de chiffrement de message et de clé de type WRAP.  Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, qui spécifie les algorithmes et les tailles de clé.  Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language \(WS\-SecurityPolicy\).<br /><br /> La valeur par défaut est `Basic256`.|  
|clientCredentialType|Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur les messages.  La valeur par défaut est `UserName`.|  
  
## Attribut clientCredentialType  
  
|Valeur|Description|  
|------------|-----------------|  
|UserName|-   Impose que le client soit authentifié auprès du serveur avec une information d'identification UserName.  Ces informations d'identification doivent être spécifiées à l'aide de l'élément \<`clientCredentials`\>.<br />-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ne prend pas en charge l'envoi d'un mot de passe Digest ou de clés dérivantes à l'aide des mots de passe et de ces clés pour la sécurité de message.  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] s'assure ainsi que le transport est sécurisé lors de l'utilisation d'informations d'identification UserName.  Pour le `basicHttpBinding`, cela requiert la configuration d'un canal SSL.|  
|Certificat|Requiert que le client soit authentifié auprès du serveur à l'aide d'un certificat.  Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide de \<`clientCredentials`\> et de \<`clientCertificate`\>.  De plus, lors de l'utilisation du mode de sécurité du message, le client doit être configuré avec le certificat du service.  Dans ce cas, les informations d'identification du service doivent être spécifiées à l'aide de la classe <xref:System.ServiceModel.Description.ClientCredentials> ou de l'élément de comportement `ClientCredentials` en spécifiant le certificat de service à l'aide de l'élément \<serviceCertificate\> de serviceCredentials.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<Élément \<`security`\> de \<`netHttpBinding`\>|Définit les fonctionnalités de sécurité pour l'élément \<`netHttpBinding`\>.|  
  
## Exemple  
 Cet exemple montre comment implémenter une application qui utilise le basicHttpBinding et la sécurité de message.  Dans l'exemple de configuration suivant pour un service, la définition du point de terminaison spécifie le basicHttpBinding et référence une configuration de liaison nommée `Binding1`.  Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section `behaviors` du fichier de configuration sous l'élément `serviceCredentials`.  Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section `behaviors` sous l'élément `clientCertificate`.  
  
 Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.  
  
```  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.NetHttpMessageSecurity>   
 <xref:System.ServiceModel.Configuration.NetHttpSecurityElement.Message%2A>   
 <xref:System.ServiceModel.NetHttpSecurity.Message%2A>   
 <xref:System.ServiceModel.Configuration.NetHttpMessageSecurityElement>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)