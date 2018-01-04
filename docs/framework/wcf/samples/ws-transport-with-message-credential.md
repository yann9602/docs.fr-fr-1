---
title: WS Transport With Message Credential
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f782ac12c92755eb26eddd30c5d8c15168c35858
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transport-with-message-credential"></a>WS Transport With Message Credential
Cet exemple montre l'utilisation de la sécurité de transport SSL en association avec les informations d'identification du client contenues dans le message. Cet exemple utilise la liaison `wsHttpBinding`.  
  
 Par défaut, la liaison `wsHttpBinding` assure la communication HTTP. En cas de configuration pour la sécurité du transport, la liaison prend en charge la communication HTTPS. HTTPS assure la protection de la confidentialité et de l'intégrité des messages transmis sur le réseau. Toutefois l'ensemble des mécanismes d'authentification qui peuvent être utilisés pour authentifier le client auprès du service est limité à ceux pris en charge par le protocole HTTPS. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] offre un mode de sécurité `TransportWithMessageCredential` conçu pour passer outre cette limitation. Lorsque ce mode de sécurité est configuré, la sécurité du transport est utilisée pour assurer la confidentialité et l'intégrité des messages transmis et procéder à l'authentification du service. Toutefois, l’authentification du client est effectuée en plaçant les informations d’identification client directement dans le message. Cela vous permet d’utiliser n’importe quel type d’informations d’identification qui est pris en charge par le mode de sécurité de message pour l’authentification du client tout en conservant l’avantage du mode de sécurité de transport.  
  
 Dans cet exemple, un type d'information d'identification `UserName` est utilisé pour authentifier le client auprès du service.  
  
 Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice. La liaison `wsHttpBinding` est spécifiée et configurée dans les fichiers de configuration de l'application pour le client et le service.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le code de programme dans l’exemple est presque identique à celui de la [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) service. Il y a une opération supplémentaire fournie par le contrat de service : `GetCallerIdentity`. Cette opération retourne le nom de l'identité de l'appelant à l'appelant.  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 Vous devez créer un certificat et l’assigner en utilisant l’Assistant Certificat de serveur web avant de générer et exécuter l’exemple. La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration activent le mode de sécurité `TransportWithMessageCredential`, comme le montre l'exemple de configuration suivant pour le client.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 L'adresse spécifiée utilise le modèle https://. La configuration de la liaison définit le mode de sécurité au mode `TransportWithMessageCredential`. Le même mode de sécurité doit être spécifié dans le fichier Web.config du service.  
  
 Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert.exe, une alerte de sécurité apparaît lorsque vous essayez d'accéder à une adresse https: telle que https://localhost/servicemodelsamples/service.svc, depuis votre navigateur. Pour permettre au client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'utiliser un certificat de test en vigueur, du code supplémentaire a été ajouté au client pour supprimer l'alerte de sécurité. Ce code, et la classe qui l'accompagne, n'est pas requis lors de l'utilisation de certificats de production.  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Assurez-vous d’avoir effectué la [Instructions d’Installation du certificat serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi
