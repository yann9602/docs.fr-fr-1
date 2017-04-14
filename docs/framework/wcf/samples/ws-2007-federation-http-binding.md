---
title: "WS 2007 Federation HTTP Binding | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# WS 2007 Federation HTTP Binding
Cet exemple montre l'utilisation de <xref:System.ServiceModel.WS2007FederationHttpBinding>, une liaison standard vous permettant de générer des scénarios fédérés qui prennent en charge la version 1.3 de la spécification WS\-Trust.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 L'exemple se compose d'un programme client basé sur des console \(Client.exe\), d'un programme de service d'émission de jeton de sécurité basé sur des consoles \(Securitytokenservice.exe\) et d'un programme de service basé sur des consoles \(Service.exe\).Le service implémente un contrat qui définit un modèle de communication demande\/réponse.Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques \(`Add`, `Subtract`, `Multiply` et `Divide`\).Le client obtient un jeton de sécurité du service d'émission de jeton de sécurité \(STS, Security Token Service\) et adresse des demandes synchrones au service pour une opération mathématique donnée.Le service répond ensuite avec le résultat.L'activité du client est visible dans la fenêtre de console.  
  
 L'exemple rend le contrat `ICalculator` disponible à l'aide de l'élément `ws2007FederationHttpBinding`.La configuration de cette liaison sur le client est présentée dans le code suivant.  
  
```  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
  
```  
  
 Sur [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), la valeur `security` spécifie le mode de sécurité à utiliser.Dans cet exemple, la sécurité `message` est utilisée ; c'est pourquoi [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) est spécifié à l'intérieur de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).L'élément [\<issuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) dans l'élément message de ws2007FederationHttpBinding \(voir [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)\) spécifie l'adresse et la liaison du STS qui émet un jeton de sécurité au client afin de lui permettre de s'authentifier auprès du service `ICalculator`.  
  
 La configuration de cette liaison sur le service est présentée dans le code suivant.  
  
```  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
  
```  
  
 Sur [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), la valeur `security` spécifie le mode de sécurité à utiliser.Dans cet exemple, la sécurité `message` est utilisée ; c'est pourquoi [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) est spécifié à l'intérieur de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).L'élément [\<issuerMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) de `ws2007FederationHttpBinding` dans l'élément message de ws2007FederationHttpBinding \(voir [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)\) spécifie l'adresse et l'identité d'un point de terminaison qui permet de récupérer les métadonnées pour le STS.  
  
 Le comportement du service est présenté dans le code suivant.  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
 [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)\> permet au service de spécifier les contraintes des jetons que les clients sont autorisés à présenter pendant leur authentification.Cette configuration spécifie que les jetons signés par un certificat dont le nom du sujet est CN\=STS sont acceptés par le service.  
  
 STS rend un point de terminaison unique disponible à l'aide du <xref:System.ServiceModel.WS2007HttpBinding> standard.Le service répond aux demandes de jeton des clients.Si le client est authentifié à l'aide d'un compte Windows, le service émet un jeton qui contient le nom d'utilisateur du client sous forme d'une revendication.Dans le cadre de la création du jeton, le STS le signe à l'aide de la clé privée associée au certificat CN\=STS.Par ailleurs, il crée une clé symétrique et la chiffre à l'aide de la clé publique associée au certificat CN\=localhost.Lorsqu'il retourne le jeton au client, le STS retourne également la clé symétrique.Le client présente le jeton émis au service `ICalculator` et prouve qu'il connaît la clé symétrique en signant le message à l'aide de celle\-ci.  
  
 Lorsque vous exécutez l'exemple, la demande de jeton de sécurité s'affiche dans la fenêtre de console du STS.Les demandes et réponses de l'opération s'affichent dans les fenêtres de console du client et du service.Appuyez sur ENTER dans l'une ou l'autre de ces fenêtres pour arrêter l'application.  
  
 `Add(100,15.99) = 115.99`  
  
 `Subtract(145,76.54) = 68.46`  
  
 `Multiply(9,81.25) = 731.25`  
  
 `Divide(22,7) = 3.14285714285714`  
  
 `Press <ENTER> to terminate client.`  
  
 Le fichier Setup.bat inclus avec cet exemple vous permet de configurer le serveur et le STS avec les certificats appropriés pour exécuter une application auto\-hébergée.Il crée deux certificats dans le magasin de certificats LocalMachine\/TrustedPeople.Le nom du sujet du premier certificat est CN\=STS. Ce certificat est utilisé par le STS pour signer les jetons de sécurité qu'il émet au client.Le nom du sujet du deuxième certificat est CN\=localhost. Ce certificat est utilisé par le STS pour chiffrer une clé de sorte que le service puisse la déchiffrer.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Ouvrez une invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez le fichier Setup.bat pour créer les certificats requis.  
  
 Ce fichier batch utilise Certmgr.exe et Makecert.exe, qui sont fournis avec le Kit de développement Windows SDK.Toutefois, vous devez exécuter Setup.bat à partir d'une invite de commandes de Visual Studio Tools pour permettre au script d'identifier ces outils.  
  
1.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).Si vous utilisez [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], vous devez exécuter Service.exe, Client.exe et SecurityTokenService.exe avec des privilèges élevés \(cliquez avec le bouton droit sur les fichiers, puis cliquez sur **Exécuter en tant qu'administrateur**\).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## Voir aussi