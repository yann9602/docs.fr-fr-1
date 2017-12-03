---
title: "Comment : authentifier à l'aide d'un nom d'utilisateur et d'un mot de passe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31e05709465e429445a2ebdafae719c24d316c8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Comment : authentifier à l'aide d'un nom d'utilisateur et d'un mot de passe
Cette rubrique montre comment permettre à un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] d'authentifier un client à l'aide d'un nom d'utilisateur et d'un mot de passe Windows. Elle suppose que vous disposez d'un service WCF auto-hébergé fonctionnel. Pour obtenir un exemple de création d’un base consultez de service WCF auto-hébergé, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md). Cette rubrique suppose que le service est configuré dans le code. Si vous souhaitez voir un exemple de configuration d’un service similaire à l’aide d’un fichier de configuration voir [nom d’utilisateur de sécurité de Message](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Pour configurer un service pour authentifier ses clients à l’aide d’utilisation de nom d’utilisateur et mots de passe de domaine Windows du <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> et définissez son `Security.Mode` propriété `Message`. En outre, vous devez spécifier un certificat X509 qui sera utilisé pour chiffrer le nom d'utilisateur et le mot de passe lors de leur envoi du client au service.  
  
 Sur le client, vous devez demander à l'utilisateur le nom d'utilisateur et le mot de passe et spécifier les informations d'identification de l'utilisateur sur le proxy WCF.  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Pour configurer un service WCF pour l'authentification à l'aide du nom d'utilisateur et du mot de passe de domaine Windows.  
  
1.  Créez une instance de la <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, définir le mode de sécurité de la liaison à `SecurityMode.Message`, définissez le `ClientCredentialType` de la liaison à `MessageCredentialType.UserName`et ajoutez un point de terminaison de service à l’aide de la liaison configurée à l’hôte de service comme indiqué dans le code suivant :  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Spécifiez le certificat de serveur utilisé pour chiffrer les informations de nom d'utilisateur et mot de passe envoyées sur le réseau. Ce code doit suivre immédiatement le code ci-dessus. L’exemple suivant utilise le certificat qui est créé par le fichier setup.bat à partir de la [nom d’utilisateur de sécurité de Message](../../../../docs/framework/wcf/samples/message-security-user-name.md) exemple :  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Vous pouvez utiliser votre propre certificat ; il vous suffit de modifier le code pour faire référence à votre certificat. Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Assurez-vous que le certificat se trouve dans le magasin de certificats Personnes approuvées de l'ordinateur local. Cela, exécutez mmc.exe et sélectionnez le **fichier**, **ajouter/supprimer un composant logiciel enfichable...**  élément de menu. Dans le **ajouter ou supprimer des composants logiciel enfichables** boîte de dialogue, sélectionnez le **enfichable Certificats** et cliquez sur **ajouter**. Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **compte d’ordinateur**. Par défaut, le certificat généré à partir de l’exemple de nom d’utilisateur de sécurité du message se trouve dans le dossier Personal/Certificates.  Il est répertorié comme « localhost » sous la colonne dans la fenêtre MMC publié. Faites glisser et déposez le certificat dans le **personnes** dossier. Cela permettra à WCF de traiter le certificat comme un certificat approuvé lorsque vous effectuez l'authentification.  
  
### <a name="to-call-the-service-passing-username-and-password"></a>Pour appeler le service en passant le nom d'utilisateur et le mot de passe  
  
1.  L'application cliente doit demander à l'utilisateur d'entrer son nom d'utilisateur et son mot de passe. Le code suivant demande à l'utilisateur le nom d'utilisateur et le mot de passe.  
  
    > [!WARNING]
    >  Ce code ne doit pas être utilisé en production, car le mot de passe s'affiche lorsqu'il est entré.  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  Créez une instance du proxy client spécifiant les informations d'authentification du client comme indiqué dans le code suivant :  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [Sécurité de transport avec l’authentification de base](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [Sécurité des applications distribuées](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
