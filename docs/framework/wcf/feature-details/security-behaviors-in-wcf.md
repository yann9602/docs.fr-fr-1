---
title: "Comportements de s&#233;curit&#233; dans WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# Comportements de s&#233;curit&#233; dans WCF
Dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], les comportements modifient le comportement au moment de l'exécution au niveau du service ou du point de terminaison.\([!INCLUDE[crabout](../../../../includes/crabout-md.md)] les comportements en général, consultez [Spécification du comportement du service au moment de l'exécution](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).\) Les *comportements de sécurité* autorisent le contrôle sur les informations d'identification, l'authentification, l'autorisation et les journaux d'audit.Vous pouvez les utiliser via la programmation ou la configuration.Cette rubrique se concentre sur la configuration des comportements relatifs aux fonctions de sécurité suivants :  
  
-   [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), qui vous permet également de spécifier un point de terminaison sécurisé auquel les clients peuvent accéder pour les métadonnées.  
  
## Définition d'informations d'identification avec des comportements  
 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) et [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) vous permettent de définir des valeurs d'informations d'identification pour un service ou un client.La configuration de liaison sous\-jacente détermine si une information d'identification doit être définie.Par exemple, si le mode de sécurité a la valeur `None`, les clients et les services ne s'authentifient pas l'un l'autre et ne requièrent pas d'information d'identification d'aucun type.  
  
 En revanche, la liaison de service peut requérir un type d'informations d'identification du client.Dans ce cas, il peut s'avérer nécessaire de définir une valeur d'information d'identification à l'aide d'un comportement.\([!INCLUDE[crabout](../../../../includes/crabout-md.md)] les types d'informations d'identification possibles, consultez [Sélection d'un type d'informations d'identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).\) Dans certains cas, par exemple lorsque des informations d'identification Windows sont utilisées pour l'authentification, l'environnement établit automatiquement la valeur d'informations d'identification réelle, et il n'est donc pas nécessaire de la définir explicitement \(sauf si vous souhaitez spécifier un autre ensemble d'informations d'identification\).  
  
 Toutes les informations d'identification du service apparaissent comme des éléments enfants de [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md).L'exemple suivant présente un certificat utilisé en tant qu'information d'identification du service.  
  
```  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## Informations d'identification du service  
 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) contient quatre éléments enfants.Les éléments et leurs utilisations sont traités dans les sections suivantes.  
  
### Élément \<serviceCertificate\>  
 Cet élément vous permet de spécifier un certificat X.509 qui est utilisé pour authentifier le service auprès des clients à l'aide du mode de sécurité Message.Si vous utilisez un certificat qui est périodiquement renouvelé, son empreinte numérique change.Dans ce cas, utilisez le nom du sujet comme `X509FindType` car le certificat peut être réémis avec le même nom du sujet.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de cet élément, consultez [Comment : spécifier des valeurs d'informations d'identification du client](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### Élément \<certificate\> de \<clientCertificate\>  
 Utilisez l'élément [\<certificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) lorsque le service doit avoir le certificat du client à l'avance afin de communiquer de manière sécurisée avec le client.Cela se produit lors de l'utilisation du modèle de communication duplex.Dans le modèle demande\-réponse plus classique, le client inclut son certificat dans la demande, que le service utilise pour sécuriser de nouveau sa réponse au client.Toutefois, le modèle de communication duplex n'a pas de demande et de réponse.Le service ne peut pas déduire le certificat du client de la communication, et par conséquent, il en a besoin à l'avance pour sécuriser les messages au client.Vous devez obtenir le certificat du client hors bande et l'indiquer à l'aide de cet élément.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les services duplex, consultez [Comment : créer un contrat duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### Élément \<authentication\>, de \<clientCertificate\>  
 L'élément [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) vous permet de personnaliser la manière dont les clients sont authentifiés.Vous pouvez affecter `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust` ou `Custom` à l'attribut `CertificateValidationMode`.Par défaut, le niveau a la valeur `ChainTrust`, laquelle spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une *autorité racine* au sommet de la chaîne.C'est le mode le plus sécurisé.Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto\-émis \(approbation homologue\) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto\-émis auprès d'une autorité approuvée.Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.Vous pouvez également utiliser `Custom`.Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `CustomCertificateValidatorType`.Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  
  
### Élément \<issuedTokenAuthentication\>  
 Le scénario de jeton émis comporte trois étapes.Au cours de la première étape, un client qui essaie d'accéder à un service est désigné par le terme de *service de jeton sécurisé* \(STS\).Le STS authentifie le client et émet ensuite un jeton pour ce dernier, généralement un jeton SAML \(Security Assertions Markup Language\).Le client retourne ensuite au service avec le jeton.Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.L'élément [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) est la base de données de référentiel pour les certificats de service d'émission de jeton sécurisé de ce type.Pour ajouter des certificats, utilisez [\<knownCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).Insérez [\<ajouter\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pour chaque certificat, tel qu'indiqué dans l'exemple suivant.  
  
```  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.  
  
 Vous devez utiliser la collection [\<allowedAudienceUris\>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) dans une application fédérée qui utilise un *service de jeton de sécurité* \(STS\) qui émet des jetons de sécurité `SamlSecurityToken`.Lorsque le STS émet le jeton de sécurité, il peut spécifier l'URI des services Web pour lesquels le jeton de sécurité est prévu en ajoutant à ce dernier une `SamlAudienceRestrictionCondition`.Cela permet au `SamlSecurityTokenAuthenticator` du service Web destinataire de vérifier que le jeton de sécurité émis est prévu pour ce service Web en spécifiant que ce contrôle doit arriver en effectuant les opérations suivantes :  
  
-   Affectez à l'attribut `audienceUriMode` de [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) la valeur `Always` ou `BearerKeyOnly`.  
  
-   Spécifiez le jeu d'URI valides en ajoutant les URI à cette collection.Pour cela, insérez un [\<ajouter\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) pour chaque URI.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de cet élément de configuration, consultez [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### Autorisation d'accès aux utilisateurs CardSpace anonymes  
 L'affectation de `true` à l'attribut `AllowUntrustedRsaIssuers` de l'élément `<IssuedTokenAuthentication>` permet aux clients de présenter un jeton auto\-émis signé avec une paire de clés RSA arbitraire.L'émetteur est *non approuvé* car la clé n'est pas associée à des données d'émetteur.Un utilisateur [!INCLUDE[infocard](../../../../includes/infocard-md.md)] peut créer une carte auto\-émise incluant des revendications d'identité auto\-fournies.Utilisez cette fonction avec précaution.Pour utiliser cette fonctionnalité, considérez la clé publique RSA comme un mot de passe plus sécurisé qui doit être stocké dans une base de données avec un nom d'utilisateur.Avant d'autoriser l'accès d'un client au service, vérifiez la clé publique RSA présentée par celui\-ci en le comparant avec celle stockée pour le nom d'utilisateur présenté.Cela suppose que vous ayez établi un processus d'inscription permettant aux utilisateurs d'enregistrer leurs noms d'utilisateur et de les associer avec les clés publiques RSA auto\-émises.  
  
## Informations d'identification du client  
 Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise.Vous pouvez utiliser la section pour spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.  
  
 Vous pouvez également configurer un client dans le cadre d'un scénario de fédération afin d'utiliser des jetons émis par un service d'émission de jeton sécurisé ou un émetteur local de jetons.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les scénarios fédérés, consultez [Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).Toutes les informations d'identification du client se trouvent sous [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), tel qu'indiqué dans le code suivant.  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### Élément \<clientCertificate\>  
 Définissez le certificat utilisé pour authentifier le client avec cet élément.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : spécifier des valeurs d'informations d'identification du client](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### \<httpDigest\>  
 Cette fonction doit être activée avec Active Directory sur Windows et les services IIS \(Internet Information Services\).[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Authentification Digest dans IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443) \(page pouvant être en anglais\).  
  
#### Élément \<issuedToken\>  
 [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) contient les éléments permettant de configurer un émetteur local de jetons, ou les comportements utilisés avec un service d'émission de jeton de sécurité.Pour obtenir des instructions sur la configuration d'un client pour qu'il utilise un émetteur local, consultez [Comment : configurer un émetteur local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### \<localIssuerAddress\>  
 Spécifie une adresse de service d'émission de jeton de sécurité par défaut.Cet élément est utilisé lorsque <xref:System.ServiceModel.WSFederationHttpBinding> ne fournit pas d'URL pour le service d'émission de jeton de sécurité, ou lorsque l'adresse de l'émetteur d'une liaison fédérée est http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous ou `null`.Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l'adresse de l'émetteur local et la liaison à utiliser pour communiquer avec celui\-ci.  
  
#### \<issuerChannelBehaviors\>  
 [\<issuerChannelBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) vous permet d'ajouter des comportements de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisés lors de la communication avec un service d'émission de jeton de sécurité.Définissez des comportements de client dans la section [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).Pour utiliser un comportement défini, ajoutez un élément \<`add`\> à l'élément `<issuerChannelBehaviors>` avec deux attributs.Affectez l'URL du service d'émission de jeton de sécurité à `issuerAddress`, et affectez le nom du comportement de point de terminaison défini à l'attribut `behaviorConfiguration`, tel qu'indiqué dans l'exemple suivant.  
  
```  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### Élément \<serviceCertificate\>  
 Cet élément vous permet de contrôler l'authentification des certificats de service.  
  
 L'élément [\<defaultCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) peut stocker un certificat unique utilisé lorsque le service ne spécifie aucun certificat.  
  
 [\<scopedCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) et [\<ajouter\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) vous permettent de définir des certificats de service associés aux services spécifiques.L'élément `<add>` inclut un attribut `targetUri` permettant d'associer le certificat au service.  
  
 L'élément [\<authentification\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) spécifie le niveau de confiance utilisé pour authentifier les certificats.Par défaut, le niveau a la valeur « ChainTrust », laquelle spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.C'est le mode le plus sécurisé.Vous pouvez également affecter la valeur « PeerOrChainTrust », laquelle spécifie que les certificats auto\-émis \(approbation homologue\) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto\-émis auprès d'une autorité approuvée.Lorsque vous déployez un client, utilisez à la place la valeur "ChainTrust".Vous pouvez également affecter "Custom" ou "None". Pour utiliser la valeur "Custom", vous devez également définir l'attribut `CustomCertificateValidatorType` à un assembly et à un type utilisés pour valider le certificat.Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 L'élément [\<authentification\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) inclut un attribut `RevocationMode` qui spécifie la manière dont les certificats sont vérifiés pour révocation.La valeur par défaut est « online », laquelle indique que les certificats sont automatiquement vérifiés pour révocation.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## ServiceAuthorization  
 L'élément [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.  
  
 La classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliquée à une méthode de service.L'attribut spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée.La valeur par défaut est "UseWindowsGroups", laquelle spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, tels que "Administrators" ou "Users".Vous pouvez également spécifier « UseAspNetRoles » pour utiliser un fournisseur de rôles personnalisé configuré sous l'élément \<`system.web` \>, tel qu'indiqué dans le code suivant.  
  
```  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Le code suivant présente le `roleProviderName` utilisé avec l'attribut `principalPermissionMode`.  
  
```  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## Configuration des audits de sécurité  
 [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) permet de spécifier le journal à utiliser et les types des événements à enregistrer.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## Échange de métadonnées sécurisé  
 L'exportation des métadonnées vers des clients s'avère pratique pour les développeurs de service et de client car elle permet des téléchargements de la configuration et du code client.Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS \(SSL over HTTP\).Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service.\([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).\) Puis, ajoutez un [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à la configuration du service et affectez `true` à l'attribut `HttpsGetEnabled`.Enfin, affectez l'attribut `HttpsGetUrl` à l'URL du point de terminaison de métadonnées du service, tel qu'illustré dans l'exemple suivant.  
  
```  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## Voir aussi  
 [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)