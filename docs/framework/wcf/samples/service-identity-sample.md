---
title: "Service Identity, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# Service Identity, exemple
Cet exemple montre comment définir l'identité d'un service.Au moment du design, un client peut récupérer l'identité à l'aide des métadonnées du service, puis au miment de l'exécution, il peut authentifier l'identité du service.Le concept d'identité de service consiste à permettre à un client d'authentifier un service avant d'appeler l'une de ses opérations, ce qui protège le client contre les appels non authentifiés.Sur une connexion sécurisée, le service authentifie également les informations d'identification d'un client avant de lui autoriser l'accès, mais ce n'est pas l'objet traité dans cet exemple.Pour plus d'informations sur l'authentification du serveur, consultez les exemples indiqués dans [Client](../../../../docs/framework/wcf/samples/client.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple illustre les fonctionnalités suivantes :  
  
-   Comment définir les divers types d'identité sur différents points de terminaison d'un service.Chaque type d'identité possède des fonctionnalités différentes.Le type d'identité à utiliser dépend du type d'informations d'identification de sécurité utilisé sur la liaison du point de terminaison.  
  
-   L'identité peut être définie de façon déclarative dans la configuration ou de façon impérative dans le code.Pour le client et le service, vous devez généralement utiliser la configuration.  
  
-   Comment définir une identité personnalisée sur le clientUne identité personnalisée est en général une personnalisation d'un type d'identité existant qui permet au client d'examiner d'autres informations de revendication fournies dans les informations d'identification du service afin de prendre des décisions d'autorisation avant d'appeler le service.  
  
    > [!NOTE]
    >  Cet exemple vérifie l'identité d'un certificat spécifique appelé identity.com et la clé RSA contenue dans ce certificat.Lors de l'utilisation des types d'identité Certificat et RSA dans la configuration sur le client, l'une des méthodes utilisées pour obtenir facilement ces valeurs consiste à inspecter le WSDL du service dans lequel ces valeurs sont sérialisées.  
  
 L'exemple de code suivant montre comment configurer l'identité d'un point de terminaison de service avec le serveur DNS \(Domain Name Server\) d'un certificat à l'aide de WSHttpBinding.  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
  
```  
  
 L'identité peut également être spécifiée dans la configuration dans le fichier App.config.L'exemple suivant montre comment définir l'identité UPN \(User Principal Name, nom d'utilisateur principal\) pour un point de terminaison de service.  
  
```  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
  
```  
  
 Une identité personnalisée peut être définie sur le client en dérivant des classes <xref:System.ServiceModel.EndpointIdentity> et <xref:System.ServiceModel.Security.IdentityVerifier>.D'un point de vue conceptuel, la classe <xref:System.ServiceModel.Security.IdentityVerifier> peut être considérée comme étant l'équivalent client de la classe `AuthorizationManager` du service.L'exemple de code suivant présente une implémentation de `OrgEndpointIdentity`, qui stocke un nom d'organisation à faire correspondre au nom du sujet du certificat du serveur.Le contrôle d'autorisation du nom d'organisation se produit dans la méthode `CheckAccess` sur la classe `CustomIdentityVerifier`.  
  
```  
  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 Cet exemple utilise un certificat appelé identity.com qui est situé dans le dossier de solution Identity correspondant à votre langue.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### Pour exécuter l'exemple sur le même ordinateur  
  
1.  Sur [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[wv](../../../../includes/wv-md.md)], importez le fichier de certificat Identity.pfx du dossier de solution Identity dans le magasin de certificats LocalMachine\/My \(Personal\) à l'aide de l'outil enfichable MMC.Ce fichier est protégé par mot de passe.Lors de l'importation, un mot de passe vous est demandé.Tapez `xyz` dans la zone de mot de passe.Pour plus d'informations, consultez la rubrique [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).Ceci fait, exécutez Setup.bat dans une invite de commandes de Visual Studio avec des privilèges élevés, qui copie ce certificat dans le magasin CurrentUser\/Trusted People pour une utilisation sur le client.  
  
2.  Sur [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], exécutez Setup.bat à partir du dossier d'installation de l'exemple dans une fenêtre d'invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges d'administrateur.Tous les certificats requis pour l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    >  Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d'une invite de commandes de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].La variable d'environnement PATH définie dans l'invite de commandes [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.Assurez\-vous d'effacer les certificats en exécutant Cleanup.bat une fois l'exemple terminé.D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
3.  Lancez Service.exe à partir du répertoire de \\service\\bin.Vérifiez que le service indique qu'il est prêt et affiche une invite avant d'appuyer sur \<Enter\> pour terminer le service.  
  
4.  Lancez Client.exe à partir du répertoire \\client\\bin ou en appuyant sur F5 dans Visual Studio pour effectuer la génération et l'exécution.L'activité du client s'affiche sur son application de console.  
  
5.  Si le client et le service ne parviennent pas à communiquer, consultez la rubrique [Troubleshooting Tips](http://msdn.microsoft.com/fr-fr/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Avant de générer la partie cliente de l'exemple, modifiez la valeur de l'adresse de point de terminaison du service du fichier Client.cs dans la méthode `CallServiceCustomClientIdentity`.Puis générez l'exemple.  
  
2.  Créez un répertoire sur l'ordinateur de service.  
  
3.  Copiez les fichiers programme du service de \\service\\bin dans le répertoire sur l'ordinateur de service.Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
4.  Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
5.  Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
6.  Sur l'ordinateur de service, ouvrez une fenêtre d'invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez `setup.bat service`.L'exécution de `setup.bat` à l'aide de l'argument `service` crée un certificat de service portant le nom de domaine complet de l'ordinateur, puis exporte ce certificat vers un fichier nommé Service.cer.  
  
7.  Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
8.  Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.Plusieurs instances doivent être modifiées.  
  
9. Sur le client, ouvrez une fenêtre d'invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez ImportServiceCert.bat.Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser \- TrustedPeople.  
  
10. Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.  
  
11. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.Si le client et le service ne parviennent pas à communiquer, consultez la rubrique [Troubleshooting Tips](http://msdn.microsoft.com/fr-fr/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### Pour procéder au nettoyage après exécution de l'exemple  
  
-   Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    >  Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.Si vous avez exécuté des exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats sur plusieurs ordinateurs, assurez\-vous d'effacer les certificats de service installés dans le magasin CurrentUser \- TrustedPeople.Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## Voir aussi