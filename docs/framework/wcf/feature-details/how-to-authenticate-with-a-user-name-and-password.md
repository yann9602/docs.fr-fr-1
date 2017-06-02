---
title: "Comment&#160;: authentifier &#224; l&#39;aide d&#39;un nom d&#39;utilisateur et d&#39;un mot de passe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "authentification (WCF), nom d'utilisateur et mot de passe"
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Comment&#160;: authentifier &#224; l&#39;aide d&#39;un nom d&#39;utilisateur et d&#39;un mot de passe
Cette rubrique montre comment permettre à un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] d'authentifier un client à l'aide d'un nom d'utilisateur et d'un mot de passe Windows.Elle suppose que vous disposez d'un service WCF auto\-hébergé fonctionnel.Pour obtenir un exemple de création d'un service WCF auto\-hébergé de base, consultez [Didacticiel de mise en route](../../../../docs/framework/wcf/getting-started-tutorial.md).Cette rubrique suppose que le service est configuré dans le code.Pour obtenir un exemple de configuration d'un service semblable à l'aide d'un fichier de configuration, consultez [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).  
  
 Pour configurer un service afin d'authentifier ses clients à l'aide du nom d'utilisateur et du mot de passe de domaine Windows, utilisez <xref:System.ServiceModel.WSHttpBinding> et affectez la valeur `Message` à sa propriété `Security.Mode`.En outre, vous devez spécifier un certificat X509 qui sera utilisé pour chiffrer le nom d'utilisateur et le mot de passe lors de leur envoi du client au service.  
  
 Sur le client, vous devez demander à l'utilisateur le nom d'utilisateur et le mot de passe et spécifier les informations d'identification de l'utilisateur sur le proxy WCF.  
  
### Pour configurer un service WCF pour l'authentification à l'aide du nom d'utilisateur et du mot de passe de domaine Windows.  
  
1.  Créez une instance de <xref:System.ServiceModel.WSHttpBinding>, définissez le mode de sécurité de liaison à `SecurityMode.Message`, définissez le `ClientCredentialType` de liaison à `MessageCredentialType.UserName`, et ajoutez un point de terminaison de service à l'aide de la liaison configurée à l'hôte de service comme indiqué dans le code suivant :  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Spécifiez le certificat de serveur utilisé pour chiffrer les informations de nom d'utilisateur et mot de passe envoyées sur le réseau.Ce code doit suivre immédiatement le code ci\-dessus.L'exemple suivant utilise le certificat qui est créé par le fichier setup.bat de l'exemple [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) :  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Vous pouvez utiliser votre propre certificat ; il vous suffit de modifier le code pour faire référence à votre certificat.Pour plus d'informations sur la création et l'utilisation de certificats, consultez [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).Assurez\-vous que le certificat se trouve dans le magasin de certificats Personnes approuvées de l'ordinateur local.Pour cela, exécutez mmc.exe et sélectionnez **Fichier**, **Ajouter\/Supprimer un composant logiciel enfichable…**.Dans la boîte de dialogue **Ajouter ou supprimer des composants logiciels enfichables**, sélectionnez **Composant logiciel enfichable Certificats** et cliquez sur **Ajouter**.Dans la boîte de dialogue du composant logiciel enfichable Certificats, sélectionnez **Le compte de l'ordinateur**.Par défaut, le certificat généré à partir de l'exemple de nom d'utilisateur de sécurité du message se trouve dans le dossier Personal\/Certificates.Il est répertorié en tant que « localhost » sous la colonne Publié sous de la fenêtre de console MMC.Faites glisser le certificat dans le dossier **Personnes autorisées**.Cela permettra à WCF de traiter le certificat comme un certificat approuvé lorsque vous effectuez l'authentification.  
  
### Pour appeler le service en passant le nom d'utilisateur et le mot de passe  
  
1.  L'application cliente doit demander à l'utilisateur d'entrer son nom d'utilisateur et son mot de passe.Le code suivant demande à l'utilisateur le nom d'utilisateur et le mot de passe.  
  
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
  
## Voir aussi  
 <xref:System.ServiceModel.WsHttpBinding>   
 <xref:System.ServiceModel.WSHttpSecurity>   
 <xref:System.ServiceModel.SecurityMode>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>   
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>   
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>   
 [Sécurité de transport avec l'authentification de base](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)   
 [Sécurité des applications distribuées](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)   
 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)