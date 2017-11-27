---
title: Token Provider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 87965b8802dd770d6977154ab805889838e9c5e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="token-provider"></a>Token Provider
Cet exemple montre comment implémenter un fournisseur de jetons personnalisé. Un fournisseur de jetons dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permet de fournir des informations d'identification à l'infrastructure de sécurité. En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est fourni avec le fournisseur de jetons du gestionnaire d'informations d'identification par défaut. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est également fourni avec un fournisseur de jetons [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :  
  
-   si vous avez un magasin d'informations d'identification avec lequel ces fournisseurs de jetons ne peuvent pas fonctionner ;  
  
-   si vous souhaitez fournir votre propre mécanisme personnalisé permettant de transformer les informations d'identification entre le moment où l'utilisateur fournit les détails et celui où l'infrastructure cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] les utilise ;  
  
-   si vous générez un jeton personnalisé.  
  
 Cet exemple montre comment générer un fournisseur de jetons personnalisé qui convertit les entrées de l'utilisateur dans un autre format.  
  
 En résumé, cet exemple montre :  
  
-   la façon dont un client peut s'authentifier à l'aide d'une paire nom d'utilisateur/mot de passe ;  
  
-   la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;  
  
-   la façon dont le serveur peut valider les informations d'identification du client à l'aide d'un mot de passe avec un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé qui valide que le nom d'utilisateur et le mot de passe correspondent ;  
  
-   la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.  
  
 Cet exemple montre également comment l'identité de l'appelant est accessible après le processus d'authentification du jeton personnalisé.  
  
 Le service expose un point de terminaison unique permettant de communiquer avec le service, défini à l'aide du fichier de configuration App.config. Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. La liaison est configurée avec un `wsHttpBinding`standard, qui utilise par défaut le mode de sécurité du message. Cet exemple définit le `wsHttpBinding` standard pour permettre l'authentification du client à l'aide du nom d'utilisateur. Le service configure également le certificat de service à l'aide du comportement serviceCredentials. Le comportement serviceCredentials vous permet de configurer un certificat de service. Un certificat de service est utilisé par un client pour authentifier le service et fournir la protection des messages. La configuration suivante référence le certificat localhost installé pendant l'installation de l'exemple, tel que décrit dans les instructions d'installation suivantes.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 La configuration de point de terminaison de client se compose d'un nom de configuration, d'une adresse absolue pour le point de terminaison de service, de la liaison et du contrat. La liaison de client est configurée avec le `Mode` et le message `clientCredentialType` appropriés.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="http://localhost:8000/servicemodelsamples/service"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator">  
    </endpoint>  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Les étapes suivantes montrent comment développer un fournisseur de jetons personnalisé et comment l'intégrer à l'infrastructure de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
1.  Écrivez un fournisseur de jetons personnalisé.  
  
     L'exemple implémente un fournisseur de jetons personnalisé qui obtient le nom d'utilisateur et le mot de passe. Le mot de passe doit correspondre à ce nom d'utilisateur. Ce fournisseur de jetons personnalisé est uniquement fourni à des fins de démonstration et son utilisation n'est pas recommandée en cas de déploiement réel.  
  
     Pour effectuer cette tâche, le fournisseur de jetons personnalisé dérive la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>. Cette méthode crée et retourne un nouveau `UserNameSecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
        // obtain username and password from the user using console window  
        string username = GetUserName();  
        string password = GetPassword();  
        Console.WriteLine("username: {0}", username);  
  
        // return new UserNameSecurityToken containing information obtained from user  
        return new UserNameSecurityToken(username, password);  
    }  
    ```  
  
2.  Écrivez un gestionnaire de jetons de sécurité personnalisé.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour le <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> spécifique qui lui est passé dans la méthode `CreateSecurityTokenProvider`. Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et un sérialiseur de jeton, mais ceux-ci ne sont pas traités dans cet exemple. Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et substitue la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons de nom d'utilisateur personnalisé lorsque les spécifications du jeton passé indiquent qu'un fournisseur de noms d'utilisateur est demandé.  
  
    ```  
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        MyUserNameClientCredentials myUserNameClientCredentials;  
  
        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)  
            : base(myUserNameClientCredentials)  
        {  
            this.myUserNameClientCredentials = myUserNameClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // if token requirement matches username token return custom username token provider  
            // otherwise use base implementation  
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)  
            {  
                return new MyUserNameTokenProvider();  
            }  
            else  
            {  
                return base.CreateSecurityTokenProvider(tokenRequirement);  
            }  
        }  
    }  
    ```  
  
3.  Écrivez une information d'identification client personnalisée.  
  
     La classe d'informations d'identification client permet de représenter les informations d'identification qui sont configurées pour le proxy client et crée le gestionnaire de jetons de sécurité utilisé pour obtenir des authentificateurs, des fournisseurs et un sérialiseur de jeton.  
  
    ```  
    public class MyUserNameClientCredentials : ClientCredentials  
    {  
        public MyUserNameClientCredentials()  
            : base()  
        {  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new MyUserNameClientCredentials();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            // return custom security token manager  
            return new MyUserNameSecurityTokenManager(this);  
        }  
    }  
    ```  
  
4.  Configurez le client pour qu'il utilise les informations d'identification du client personnalisées.  
  
     Pour que le client puisse utiliser les informations d'identification client personnalisées, l'exemple supprime la classe d'informations d'identification client par défaut et fournit la nouvelle.  
  
    ```  
    static void Main()  
    {  
        // ...  
           // Create a client with given client endpoint configuration  
          CalculatorClient client = new CalculatorClient();  
  
          // set new credentials  
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());  
       // ...  
    }  
    ```  
  
 Sur le service, utilisez <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> tel qu'indiqué dans l'exemple de code suivant pour afficher les informations de l'appelant. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contient des informations sur les revendications relatives à l'appelant actuel.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
## <a name="setup-batch-file"></a>Fichier de commandes d'installation  
 Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec le certificat approprié pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur. Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.  
  
 Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :  
  
-   Création du certificat de serveur  
  
     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable `%SERVER_NAME%` spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut dans ce fichier de commandes est localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Installation du certificat de serveur dans le magasin de certificats approuvés du client :  
  
     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK. La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK. Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1.  Ouvrez une fenêtre d'invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges d'administrateur et exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    >  Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d'une invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. La variable d'environnement PATH définie dans l'invite de commandes [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.  
  
2.  Lancez service.exe à partir de service\bin.  
  
3.  Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4.  À l'invite de nom d'utilisateur, tapez un nom d'utilisateur.  
  
5.  À l'invite de mot de passe, utilisez la même chaîne tapée pour l'invite de nom d'utilisateur.  
  
6.  Si le client et le service ne parviennent pas à communiquer, consultez [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.  
  
2.  Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service. Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
3.  Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur. Le fichier Service.exe.config doit être mis à jour pour refléter ce nouveau nom de certificat. Vous pouvez créer le certificat de serveur en modifiant le fichier de commandes Setup.bat. Notez que vous devez exécuter le fichier Setup.bat à partir d'une fenêtre d'invite de commandes de Visual Studio ouverte avec des privilèges d'administrateur. Vous devez affecter à la variable `%SERVER_NAME%` le nom d'hôte complet de l'ordinateur utilisé pour héberger le service.  
  
4.  Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client. Cette opération n'est pas nécessaire lorsque le certificat de serveur est émis par un émetteur approuvé du client.  
  
5.  Dans le fichier Service.exe.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base pour spécifier le nom de l'ordinateur complet au lieu de localhost.  
  
6.  Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.  
  
7.  Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l'ordinateur client.  
  
8.  Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.  
  
9. Sur l'ordinateur client, lancez `Client.exe` à partir d'une invite de commandes.  
  
10. Si le client et le service ne parviennent pas à communiquer, consultez [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1.  Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
## <a name="see-also"></a>Voir aussi
