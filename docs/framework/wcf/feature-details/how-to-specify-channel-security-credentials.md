---
title: "Comment : spécifier des informations d'identification pour la sécurité des canaux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-channel-security-credentials"></a>Comment : spécifier des informations d'identification pour la sécurité des canaux
Le moniker de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permet aux applications COM d'appeler des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. La plupart des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requièrent que le client spécifie des informations d'identification pour l'authentification et l'autorisation. Lorsque vous appelez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez spécifier ces informations d'identification en code managé ou dans un fichier de configuration de l'application. Lorsque vous appelez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] depuis une application COM, vous pouvez utiliser l'interface <xref:System.ServiceModel.ComIntegration.IChannelCredentials> pour spécifier les informations d'identification. Cette rubrique illustre diverses méthodes pour spécifier des informations d'identification à l'aide de l'interface <xref:System.ServiceModel.ComIntegration.IChannelCredentials>.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> est une interface basée sur IDispatch et vous ne rencontrerez pas de fonctionnalités IntelliSense dans l'environnement Visual Studio.  
  
 Cet article utilisera le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service défini dans le [Message Security, exemple](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Pour spécifier un certificat client  
  
1.  Exécutez le fichier Setup.bat dans le répertoire de la sécurité de message pour créer et installer les certificats de test requis.  
  
2.  Ouvrez le projet de la sécurité de message.  
  
3.  Ajouter `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` à la `ICalculator` définition d’interface.  
  
4.  Ajouter `bindingNamespace=``http://Microsoft.ServiceModel.Samples` à la balise de point de terminaison dans le fichier App.config pour le service.  
  
5.  Générez l'exemple de la sécurité de message et exécutez Service.exe. Utilisez Internet Explorer et naviguez jusqu'à l'URI du service (http://localhost:8000/ServiceModelSamples/Service) pour vérifier que le service fonctionne.  
  
6.  Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard. Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  Exécutez l'application Visual Basic et vérifiez les résultats.  
  
     L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4). l'<xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> peut également être utilisé à la place de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> pour définir le certificat client :  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Pour que fonctionne cet appel, le certificat client doit être approuvé sur l'ordinateur qui exécute le client.  
  
> [!NOTE]
>  Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide. Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
### <a name="to-specify-user-name-and-password"></a>Pour spécifier un nom d'utilisateur et un mot de passe  
  
1.  Modifiez le fichier App.config du service pour utiliser `wsHttpBinding`. Il est requis pour la validation du nom d'utilisateur et du mot de passe :  
  
  
  
2.  Affectez `clientCredentialType` à UserName :  
  
  
  
3.  Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard. Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  Exécutez l'application Visual Basic et vérifiez les résultats. L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4).  
  
    > [!NOTE]
    >  La liaison spécifiée dans le moniker de service dans cet exemple a été remplacée par WSHttpBinding_ICalculator. Notez aussi que vous devez fournir un nom d'utilisateur et un mot de passe valides dans l'appel à <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Pour spécifier des informations d'identification Windows  
  
1.  Affectez `clientCredentialType` à Windows dans le fichier App.config de service :  
  
  
  
2.  Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard. Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  Exécutez l'application Visual Basic et vérifiez les résultats. L'application Visual Basic affiche un message contenant le résultat de l'appel Add(3, 4).  
  
    > [!NOTE]
    >  Vous devez remplacer "domain", "userID" et "password" par des valeurs valides.  
  
### <a name="to-specify-an-issue-token"></a>Pour spécifier un jeton d'émission  
  
1.  Ces jetons sont utilisés uniquement pour les applications qui utilisent la sécurité fédérée. Pour plus d’informations sur la sécurité fédérée, consultez [fédération et les jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) et [Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     L'exemple de code Visual Basic suivant montre comment appeler la méthode <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> :  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Pour plus d'informations sur les paramètres de cette méthode, consultez <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Voir aussi  
 [Fédération](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Guide pratique pour configurer des informations d’identification sur un service FS (Federation Service)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Guide pratique pour créer un client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Sécurité de message](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
