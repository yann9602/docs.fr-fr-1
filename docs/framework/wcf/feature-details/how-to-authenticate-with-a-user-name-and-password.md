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
ms.workload: dotnet
ms.openlocfilehash: 1554e8594a611aa75876d14ee7ad0689932372e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="6a0af-102">Comment : authentifier à l'aide d'un nom d'utilisateur et d'un mot de passe</span><span class="sxs-lookup"><span data-stu-id="6a0af-102">How to: Authenticate with a User Name and Password</span></span>
<span data-ttu-id="6a0af-103">Cette rubrique montre comment permettre à un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] d'authentifier un client à l'aide d'un nom d'utilisateur et d'un mot de passe Windows.</span><span class="sxs-lookup"><span data-stu-id="6a0af-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="6a0af-104">Elle suppose que vous disposez d'un service WCF auto-hébergé fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="6a0af-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="6a0af-105">Pour obtenir un exemple de création d’un base consultez de service WCF auto-hébergé, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6a0af-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="6a0af-106">Cette rubrique suppose que le service est configuré dans le code.</span><span class="sxs-lookup"><span data-stu-id="6a0af-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="6a0af-107">Si vous souhaitez voir un exemple de configuration d’un service similaire à l’aide d’un fichier de configuration voir [nom d’utilisateur de sécurité de Message](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="6a0af-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="6a0af-108">Pour configurer un service pour authentifier ses clients à l’aide d’utilisation de nom d’utilisateur et mots de passe de domaine Windows du <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> et définissez son `Security.Mode` propriété `Message`.</span><span class="sxs-lookup"><span data-stu-id="6a0af-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="6a0af-109">En outre, vous devez spécifier un certificat X509 qui sera utilisé pour chiffrer le nom d'utilisateur et le mot de passe lors de leur envoi du client au service.</span><span class="sxs-lookup"><span data-stu-id="6a0af-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="6a0af-110">Sur le client, vous devez demander à l'utilisateur le nom d'utilisateur et le mot de passe et spécifier les informations d'identification de l'utilisateur sur le proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="6a0af-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="6a0af-111">Pour configurer un service WCF pour l'authentification à l'aide du nom d'utilisateur et du mot de passe de domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="6a0af-111">To configure a WCF service to authenticate using Windows domain username and password.</span></span>  
  
1.  <span data-ttu-id="6a0af-112">Créez une instance de la <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, définir le mode de sécurité de la liaison à `SecurityMode.Message`, définissez le `ClientCredentialType` de la liaison à `MessageCredentialType.UserName`et ajoutez un point de terminaison de service à l’aide de la liaison configurée à l’hôte de service comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6a0af-112">Create an instance of the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="6a0af-113">Spécifiez le certificat de serveur utilisé pour chiffrer les informations de nom d'utilisateur et mot de passe envoyées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="6a0af-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="6a0af-114">Ce code doit suivre immédiatement le code ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="6a0af-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="6a0af-115">L’exemple suivant utilise le certificat qui est créé par le fichier setup.bat à partir de la [nom d’utilisateur de sécurité de Message](../../../../docs/framework/wcf/samples/message-security-user-name.md) exemple :</span><span class="sxs-lookup"><span data-stu-id="6a0af-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="6a0af-116">Vous pouvez utiliser votre propre certificat ; il vous suffit de modifier le code pour faire référence à votre certificat.</span><span class="sxs-lookup"><span data-stu-id="6a0af-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="6a0af-117">Pour plus d’informations sur la création et l’utilisation de certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6a0af-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="6a0af-118">Assurez-vous que le certificat se trouve dans le magasin de certificats Personnes approuvées de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6a0af-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="6a0af-119">Cela, exécutez mmc.exe et sélectionnez le **fichier**, **ajouter/supprimer un composant logiciel enfichable...**  élément de menu.</span><span class="sxs-lookup"><span data-stu-id="6a0af-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="6a0af-120">Dans le **ajouter ou supprimer des composants logiciel enfichables** boîte de dialogue, sélectionnez le **enfichable Certificats** et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6a0af-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="6a0af-121">Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **compte d’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="6a0af-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="6a0af-122">Par défaut, le certificat généré à partir de l’exemple de nom d’utilisateur de sécurité du message se trouve dans le dossier Personal/Certificates.</span><span class="sxs-lookup"><span data-stu-id="6a0af-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="6a0af-123">Il est répertorié comme « localhost » sous la colonne dans la fenêtre MMC publié.</span><span class="sxs-lookup"><span data-stu-id="6a0af-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="6a0af-124">Faites glisser et déposez le certificat dans le **personnes** dossier.</span><span class="sxs-lookup"><span data-stu-id="6a0af-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="6a0af-125">Cela permettra à WCF de traiter le certificat comme un certificat approuvé lorsque vous effectuez l'authentification.</span><span class="sxs-lookup"><span data-stu-id="6a0af-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
### <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="6a0af-126">Pour appeler le service en passant le nom d'utilisateur et le mot de passe</span><span class="sxs-lookup"><span data-stu-id="6a0af-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="6a0af-127">L'application cliente doit demander à l'utilisateur d'entrer son nom d'utilisateur et son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6a0af-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="6a0af-128">Le code suivant demande à l'utilisateur le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6a0af-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="6a0af-129">Ce code ne doit pas être utilisé en production, car le mot de passe s'affiche lorsqu'il est entré.</span><span class="sxs-lookup"><span data-stu-id="6a0af-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
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
  
2.  <span data-ttu-id="6a0af-130">Créez une instance du proxy client spécifiant les informations d'authentification du client comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6a0af-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a0af-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a0af-131">See Also</span></span>  
 <span data-ttu-id="6a0af-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="6a0af-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="6a0af-133">Sécurité de transport avec authentification de base</span><span class="sxs-lookup"><span data-stu-id="6a0af-133">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="6a0af-134">Sécurité des applications distribuées</span><span class="sxs-lookup"><span data-stu-id="6a0af-134">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="6a0af-135">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6a0af-135">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
