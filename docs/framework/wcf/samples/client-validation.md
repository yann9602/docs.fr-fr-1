---
title: Client Validation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f187e6fb64fd3bbf08b3d0b92917ffc640b02186
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="client-validation"></a>Client Validation
Les services publient fréquemment des métadonnées pour activer la génération et la configuration automatiques de types de proxy clients. Lorsque le service n'est pas approuvé, les applications clientes doivent valider que les métadonnées se conforment à la stratégie de l'application cliente en ce qui concerne la sécurité, les transactions, le type de contrat de service, etc. L'exemple suivant montre comment écrire un comportement de point de terminaison client qui valide le point de terminaison de service pour garantir que ce dernier est fiable.  
  
 Le service expose quatre points de terminaison de service. Le premier point de terminaison utilise WSDualHttpBinding, le deuxième utilise l'authentification NTLM, le troisième active le flux de transaction et le quatrième utilise l'authentification basée sur les certificats.  
  
 Le client utilise la classe <xref:System.ServiceModel.Description.MetadataResolver> pour récupérer les métadonnées pour le service. Le client met en vigueur une stratégie d'interdiction des liaisons duplex, d'authentification NTLM et de flux de transaction à l'aide d'un comportement de validation. Pour chaque instance <xref:System.ServiceModel.Description.ServiceEndpoint> importée à partir des métadonnées du service, l'application cliente ajoute une instance du comportement de point de terminaison `InternetClientValidatorBehavior` au <xref:System.ServiceModel.Description.ServiceEndpoint> avant d'essayer d'utiliser un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour se connecter au point de terminaison. La méthode `Validate` du comportement s'exécute avant qu'une opération sur le service soit appelée et met en vigueur la stratégie du client en levant `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1.  Ouvrez une invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
2.  Exécutez l'application de service à partir de \service\bin\Debug.  
  
3.  Exécutez l'application cliente à partir de \client\bin\Debug. L'activité du client s'affiche sur son application de console.  
  
4.  Si le client et le service ne parviennent pas à communiquer, consultez [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Sur le serveur, dans une invite de commandes de Visual Studio avec des privilèges d’administrateur, et tapez `setup.bat service`. En cours d’exécution `setup.bat` avec la `service` argument crée un certificat de service portant le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé Service.cer.  
  
2.  Sur le serveur, modifiez le fichier App.config en fonction du nouveau nom du certificat. Autrement dit, modifiez le `findValue` d’attribut dans le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) élément pour le nom de domaine complet de l’ordinateur.  
  
3.  Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
4.  Sur le client, ouvrez une invite de commandes Visual Studio avec des privilèges d’administrateur et le type `setup.bat client`. En cours d’exécution `setup.bat` avec la `client` argument crée un certificat client appelé Client.com et exporte le certificat client vers un fichier nommé Client.cer.  
  
5.  Dans le fichier client.cs, modifiez la valeur de l'adresse du point de terminaison MEX et `findValue` pour que le certificat de serveur par défaut corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur. Régénérez.  
  
6.  Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
7.  Sur le client, ouvrez une fenêtre d'invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez ImportServiceCert.bat. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
8.  Sur le serveur, ouvrez une fenêtre d'invite de commandes de Visual Studio avec des privilèges d'administrateur et exécutez ImportClientCert.bat. Le certificat client est ainsi importé à partir du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
9. Sur l'ordinateur de service, générez le projet de service dans Visual Studio et exécutez service.exe.  
  
10. Sur l'ordinateur client, exécutez client.exe.  
  
    1.  Si le client et le service ne parviennent pas à communiquer, consultez [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
-   Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    >  Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilisent des certificats sur plusieurs ordinateurs, assurez-vous d'effacer les certificats de service installés dans le magasin CurrentUser - TrustedPeople. Pour ce faire, utilisez la ligne de commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)
