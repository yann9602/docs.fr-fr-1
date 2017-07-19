---
title: "Message Security, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: 33
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 33
---
# Message Security, exemple
Cet exemple montre comment implémenter une application qui utilise `basicHttpBinding` et la sécurité de message.Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le mode de sécurité de `basicHttpBinding` peut avoir les valeurs suivantes : `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` et `None`.Dans l'exemple de fichier App.config de service suivant, la définition de point de terminaison spécifie `basicHttpBinding` et référence une configuration de liaison appelée `Binding1`, tel qu'indiqué dans l'exemple de configuration suivant :  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 La configuration de liaison affecte `Message` à l'attribut `mode` de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) et affecte `Certificate` à l'attribut `clientCredentialType` de [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md), tel qu'indiqué dans l'exemple de configuration suivant :  
  
```  
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
```  
  
 Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section des comportements du fichier de configuration située sous l'élément `serviceCredentials`.Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section des comportements située sous l'élément `clientCertificate`.  
  
```  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.  
  
 L'identité de l'appelant s'affiche dans la fenêtre de console du service à l'aide du code suivant :  
  
```  
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur ENTER dans la fenêtre du client pour l'arrêter.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer et générer l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### Pour exécuter l'exemple sur le même ordinateur  
  
1.  Exécutez Setup.bat à partir du dossier d'installation de l'exemple.Tous les certificats requis pour l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    >  Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d'une invite de commandes du Kit de développement Windows SDK.La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.Cette variable est définie automatiquement dans une invite de commandes du Kit de développement Windows SDK.  
  
2.  Exécutez l'application de service à partir de \\service\\bin.  
  
3.  Exécutez l'application cliente à partir de \\client\\bin.L'activité du client s'affiche sur son application de console.  
  
4.  Si le client et le service ne parviennent pas à communiquer, consultez la rubrique [Troubleshooting Tips](http://msdn.microsoft.com/fr-fr/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé.D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
### Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.  
  
2.  Copiez les fichiers programme du service dans le répertoire de service sur le serveur.Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur le serveur.  
  
3.  Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4.  Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5.  Sur le serveur, exécutez `setup.bat service`.L'exécution de `setup.bat` avec l'argument `service` crée un certificat de service portant le nom de domaine complet de l'ordinateur, puis exporte ce certificat vers un fichier appelé Service.cer.  
  
6.  Modifiez Service.exe.config afin de prendre en compte le nouveau nom de certificat \(dans l'attribut `findValue` de l'élément [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)\) qui est identique au nom de domaine complet de l'ordinateur.Modifiez également la valeur de l'adresse de base afin de remplacer localhost par un nom d'ordinateur complet`.`  
  
7.  Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.  
  
8.  Sur le client, exécutez `setup.bat client`.L'exécution de `setup.bat`  avec l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier appelé Client.cer.  
  
9. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.Remplacez également l'attribut `findValue` de [\<defaultCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) par le nouveau nom de certificat de service qui correspond au nom de domaine complet du serveur.  
  
10. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
11. Sur le client, exécutez ImportServiceCert.bat.Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser \- TrustedPeople.  
  
12. Sur le serveur, exécutez ImportClientCert.bat. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine \- TrustedPeople.  
  
13. Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.  
  
14. Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.  
  
    1.  Si le client et le service ne parviennent pas à communiquer, consultez la rubrique [Troubleshooting Tips](http://msdn.microsoft.com/fr-fr/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### Pour procéder au nettoyage après exécution de l'exemple  
  
-   Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    >  Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.Si vous avez exécuté des exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats sur plusieurs ordinateurs, assurez\-vous d'effacer les certificats de service installés dans le magasin CurrentUser \- TrustedPeople.Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## Voir aussi