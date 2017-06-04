---
title: "&lt;security&gt; de &lt;customBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
caps.latest.revision: 24
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 24
---
# &lt;security&gt; de &lt;customBinding&gt;
Spécifie les options de sécurité d'une liaison personnalisée.  
  
## Syntaxe  
  
```  
  
<security   
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
      defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
      requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
      messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean"  
      securityHeaderLayout=  
              "Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean">  
   <issuedTokenParameters />  
   <localClientSettings />  
   <localServiceSettings />  
   <secureConversationBootstrap />  
</security>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|allowSerializedSigningTokenOnReply|Facultatif.  Valeur booléenne qui spécifie si un jeton sérialisé peut être utilisé sur la réponse.  La valeur par défaut est `false`.  Si vous utilisez une liaison double, le paramètre a la valeur par défaut `true` et tout paramètre défini sera ignoré.|  
|authenticationMode|Facultatif.  Spécifie le mode d'authentification utilisé entre l'initiateur et le répondeur.  Reportez\-vous ci\-dessous pour connaître toutes les valeurs.<br /><br /> La valeur par défaut est `sspiNegotiated`.|  
|defaultAlgorithmSuite|Facultatif.  Définit les algorithmes de chiffrement de message et de clé de type WRAP.  Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language \(WS\-SecurityPolicy\).<br /><br /> Les valeurs possibles sont indiquées ci\-dessous.  La valeur par défaut est `Basic256`.<br /><br /> Cet attribut est employé lors de l'utilisation d'une plate\-forme différente qui opte pour un jeu d'algorithmes différent de la valeur par défaut.  Vous devez connaître les forces et les faiblesses des algorithmes concernés lorsque vous modifiez ce paramètre.  Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Valeur booléenne qui spécifie si les horodatages sont inclus dans chaque message.  La valeur par défaut est `true`.|  
|keyEntropyMode|Spécifie la manière dont les clés de sécurisation des messages sont calculées.  Les clés peuvent être basées uniquement sur la clé du client, sur la clé du service ou sur une combinaison des deux.  Les valeurs valides sont les suivantes :<br /><br /> -   `ClientEntropy` : la clé de la session est basée sur les données de la clé fournies par le client.<br />-   `ServerEntropy` : la clé de la session est basée sur les données de la clés fournies par le serveur.<br />-   `CombinedEntropy` : la clé de la session est basée sur les données de la clés fournies par le client et le service.<br /><br /> La valeur par défaut est `CombinedEntropy`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Définit l'ordre dans lequel les algorithmes de sécurité au niveau du message sont appliqués au message.  Les valeurs valides sont les suivantes :<br /><br /> -   `SignBeforeEncrypt` : signer en premier, chiffrer ensuite.<br />-   `SignBeforeEncryptAndEncryptSignature` : signer en premier, chiffrer, puis chiffrer la signature.<br />-   `EncryptBeforeSign` : chiffrer en premier, signer ensuite.<br /><br /> La valeur par défaut dépend de la version de WS\-Security qui est utilisée.  La valeur par défaut est `SignBeforeEncryptAndEncryptSignature` lors de l'utilisation de WS\-Security 1,1.  La valeur par défaut est `SignBeforeEncrypt` lors de l'utilisation de WS\-Security 1.0.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|Facultatif.  Définit la version de WS\-Security utilisée.  Les valeurs valides sont les suivantes :<br /><br /> -   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-   WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> La valeur par défaut est WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 et peut être simplement exprimée en XML par `Default`.  Cet attribut est de type <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Valeur booléenne qui spécifie si les clés peuvent être dérivées des clés de vérification d'origine.  La valeur par défaut est `true`.|  
|requireSecurityContextCancellation|Facultatif.  Valeur booléenne qui spécifie si le contexte de sécurité doit être annulé et arrêté lorsqu'il n'est plus exigé.  La valeur par défaut est `true`.|  
|requireSignatureConfirmation|Facultatif.  Valeur booléenne qui spécifie si la confirmation de signature WS\-Security est activée.  En cas de définition à `true`, les signatures de message sont confirmées par le répondeur.  Lorsque la liaison personnalisée est configurée pour des certificats mutuels ou si elle est configurée pour utiliser des jetons émis \(liaisons WSS 1.1\) cet attribut a la valeur par défaut `true`.  Sinon, la valeur par défaut est `false`.<br /><br /> La confirmation de signature est utilisée pour confirmer que le service répond en toute confiance à une demande.|  
|securityHeaderLayout|Facultatif.  Spécifie le classement des éléments dans l'en\-tête de sécurité.  Les valeurs valides sont les suivantes :<br /><br /> -   `Strict` : les éléments sont ajoutés à l'en\-tête de sécurité conformément au principe général "déclarer avant d'utiliser".<br />-   `Lax` : les éléments sont ajoutés à l'en\-tête de sécurité dans n'importe quel ordre conforme à WSS: SOAP Message Security.<br />-   `LaxWithTimestampFirst` : les éléments sont ajoutés à l'en\-tête de sécurité dans n'importe quel ordre conforme à WSS: SOAP Message Security, mais le premier élément de l'en\-tête de sécurité doit être un élément wsse:Timestamp.<br />-   `LaxWithTimestampLast` : les éléments sont ajoutés à l'en\-tête de sécurité dans n'importe quel ordre conforme à WSS: SOAP Message Security, mais le dernier élément de l'en\-tête de sécurité doit être un élément wsse:Timestamp.<br /><br /> La valeur par défaut est `Strict`.<br /><br /> Cet élément est de type <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## authenticationMode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Chaîne|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## defaultAlgorithm, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|Basic128|Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic192|Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic256|Utilisez le chiffrement Aes256, Sha1 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDes|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic128Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesRsa15|Utilisez le chiffrement TripleDes, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic128Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic192Sha256|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic256Sha256|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|TripleDesSha256|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa\-oaep\-mgf1p pour la clé de type WRAP.|  
|Basic128Sha256Rsa15|Utilisez Aes128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic192Sha256Rsa15|Utilisez Aes192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|Basic256Sha256Rsa15|Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
|TripleDesSha256Rsa15|Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa15 pour la clé de type WRAP.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Spécifie un jeton émis en cours.  Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Spécifie les paramètres de sécurité d'un client local pour cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Spécifie les paramètres de sécurité d'un service local pour cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap\>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] l'utilisation de cet élément, consultez [Modes d'authentification SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) et [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## Exemple  
 L'exemple suivant montre comment configurer la sécurité à l'aide d'une liaison personnalisée.  Il indique également comment utiliser une liaison personnalisée afin d'activer la sécurité de niveau message à l'aide d'un transport sécurisé.  Cette configuration est utile lorsqu'un transport sécurisé est requis pour la transmission des messages entre le client et le service et que ces messages doivent en même temps bénéficier d'une sécurité de niveau message.  Cette configuration n'est pas prise en charge par les liaisons fournies par le système.  
  
 La configuration du service définit une liaison personnalisée qui prend en charge la communication TCP protégée à l'aide du protocole TLS\/SSL et de la sécurité des messages Windows.  La liaison personnalisée utilise un certificat de service afin d'authentifier le service au niveau du transport et de protéger les messages pendant leur transmission entre le client et le service.  Cette tâche est effectuée par l'élément de liaison [\<sslStreamSecurity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md).  Le certificat du service est configuré à l'aide d'un comportement de service.  
  
 En outre, la liaison personnalisée utilise la sécurité de niveau message avec le type d'informations d'identification Windows, c'est\-à\-dire le type par défaut.  Cette tâche est effectuée par l'élément de liaison [security](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  Le client et le service sont tous deux authentifiés à l'aide de la sécurité de niveau message lorsque le mécanisme d'authentification Kerberos est disponible.  Si le mécanisme d'authentification Kerberos n'est pas disponible, l'authentification NTLM est utilisée.  NTLM authentifie le client auprès du service mais n'authentifie pas le service auprès du client.  L'élément de liaison [security](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) est configuré pour utiliser authenticationType `SecureConversation`, ce qui entraîne la création d'une session de sécurité à la fois au niveau du client et du service.  Ceci est nécessaire pour permettre au contrat duplex du service de fonctionner.  Pour plus d'informations sur l'exécution de cet exemple, consultez [Custom Binding Security](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- use following base address -->  
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                    binding="customBinding"  
                    bindingConfiguration="Binding1"   
                    contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <sslStreamSecurity requireClientCertificate="false"/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.SecurityElement>   
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Custom Binding Security](../../../../../docs/framework/wcf/samples/custom-binding-security.md)