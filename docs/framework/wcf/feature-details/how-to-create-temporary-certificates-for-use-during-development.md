---
title: "Comment : créer des certificats temporaires à utiliser au cours du développement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83f93d6bac0e16fe0b44ea5aba718ddb4dcf7c6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Comment : créer des certificats temporaires à utiliser au cours du développement
Lors du développement d'un service ou d'un client sécurisé à l'aide de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], il est souvent nécessaire de fournir un certificat X.509 à utiliser comme informations d'identification. Le certificat fait en général partie d'une chaîne de certificats dont l'autorité racine est présente dans le magasin d'Autorités de certification racines de confiance de l'ordinateur. Une chaîne de certificats vous permet de définir la portée d'un jeu de certificats où en général l'autorité racine provient de votre organisation ou votre division. Pour émuler ce scénario au moment du développement, vous pouvez créer deux certificats pour satisfaire les conditions de sécurité. Le premier est un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance. Le deuxième certificat est créé à partir du premier et placé dans le magasin personnel de l'emplacement de l'ordinateur local ou dans le magasin personnel de l'emplacement de l'utilisateur actif. Cette rubrique décrit les étapes permettant de créer ces deux certificats à l’aide de l’ [outil de création de certificat (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), fourni par le Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .  
  
> [!IMPORTANT]
>  Les certificats générés par l'outil de création de certification sont fournis uniquement à des fins de tests. Lorsque vous déployez un service ou un client, veillez à utiliser un certificat approprié fourni par une autorité de certification. Celui-ci peut provenir d'un serveur de certificat [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] dans votre organisation ou d'un tiers.  
>   
>  Par défaut, le [Makecert.exe (outil de création de certificat)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) crée des certificats dont l’autorité racine est appelée « agence de racine**. »** Comme celle-ci ne figure pas dans le magasin d'Autorités de certification racines de confiance, ces certificats ne sont pas sécurisés. La création d'un certificat auto-signé placé dans le magasin d'Autorités de certification racines de confiance vous permet de créer un environnement de développement qui reproduit plus fidèlement votre environnement de déploiement.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création et l’utilisation de certificats, consultez [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l’utilisation d’un certificat en tant qu’informations d’identification, consultez [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Pour obtenir un didacticiel à propos de l’utilisation de la technologie Authenticode de Microsoft, consultez [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919)(Vues d’ensemble et didacticiels relatifs à Authenticode).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Pour créer un certificat d'autorité racine auto-signé et exporter la clé privée  
  
1.  Utilisez l'outil MakeCert.exe avec les commutateurs suivants :  
  
    1.  `-n` `subjectName`. Spécifie le nom du sujet. La convention est de préfixer le nom du sujet avec "CN = ", abréviation de « Common Name ».  
  
    2.  `-r`. Spécifie que le certificat sera auto-signé.  
  
    3.  `-sv` `privateKeyFile`. Spécifie le fichier qui contient le conteneur de clé privée.  
  
     Par exemple, la commande suivante crée un certificat auto-signé avec un nom de sujet de "CN=TempCA".  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Le système vous invite à fournir un mot de passe pour protéger la clé privée. Ce mot de passe est requis lors de la création d'un certificat signé par ce certificat racine.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Pour créer un nouveau certificat signé par un certificat d'autorité racine  
  
1.  Utilisez l'outil MakeCert.exe avec les commutateurs suivants :  
  
    1.  `-sk` `subjectKey`. Emplacement du conteneur de clé du sujet comportant la clé privée. Un conteneur de clé sera créé s'il n'en existe aucun. Si aucune des options -sk ou -sv n'est utilisée, un conteneur de clé appelé JoeSoft est créé par défaut.  
  
    2.  `-n` `subjectName`. Spécifie le nom du sujet. La convention est de préfixer le nom du sujet avec "CN = ", abréviation de « Common Name ».  
  
    3.  `-iv` `issuerKeyFile`. Spécifie le fichier de clé privée de l'émetteur.  
  
    4.  `-ic` `issuerCertFile`. Spécifie l'emplacement du certificat de l'émetteur.  
  
     Par exemple, la commande suivante crée un certificat signé par le certificat d'autorité racine `TempCA` avec `"CN=SignedByCA"` comme nom de sujet qui utilise la clé privée de l'émetteur.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Installation d'un certificat dans le magasin d'Autorités de certification racines de confiance  
 Une fois qu'un certificat auto-signé est créé, vous pouvez l'installer dans le magasin d'Autorités de certification racines de confiance. Tous les certificats signés à ce stade avec le certificat sont approuvés par l'ordinateur. Pour cette raison, supprimez le certificat du magasin dès que vous n'en avez plus besoin. Lorsque vous supprimez ce certificat d'autorité racine, tous les autres certificats ayant signé à l'aide de ce dernier ne sont plus autorisés. Les certificats d'autorité racines sont un simple mécanisme qui permet de définir la portée d'un groupe de certificats selon les besoins. Par exemple, dans les applications d'égal à égal, l'autorité racine n'est pas nécessaire le plus souvent dans la mesure où l'identité d'un individu est garantie par le certificat qu'il fournit.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Pour installer un certificat auto-signé dans les Autorités de certification racines de confiance  
  
1.  Ouvrez le composant logiciel enfichable Certificat. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : afficher des certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Ouvrez le dossier pour stocker le certificat, soit **Ordinateur local** , soit **Utilisateur actuel**.  
  
3.  Ouvrez le dossier **Autorités de certification racines de confiance** .  
  
4.  Cliquez avec le bouton droit sur le dossier **Certificats** et cliquez sur **Toutes les tâches**, puis cliquez sur **Importer**.  
  
5.  Suivez les instructions de l'Assistant à l'écran pour importer TempCa.cer dans le magasin.  
  
## <a name="using-certificates-with-wcf"></a>Utilisation de certificats avec WCF  
 Une fois que vous avez configuré les certificats temporaires, vous pouvez les utiliser pour développer des solutions WCF qui spécifient des certificats comme un type d'informations d'identification du client. Par exemple, la configuration XML suivante spécifie la sécurité du message et un certificat comme type d'informations d'identification du client.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Pour spécifier un certificat comme type d'informations d'identification du client  
  
-   Dans le fichier de configuration d'un service, utilisez le XML suivant pour affecter au mode de sécurité la valeur Message, et au type d'informations d'identification du client la valeur Certificat.  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 Dans le fichier de configuration pour un client, utilisez le code XML suivant pour spécifier que le certificat est trouvé dans le magasin de l’utilisateur et sont accessibles via le champ SubjectName la valeur « CohoWinery ».  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 Pour plus d’informations sur l’utilisation des certificats dans WCF, consultez [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Veillez à supprimer tous les certificats d'autorité racines temporaires des dossiers **Autorités de certification racines de confiance** et **Personnel** en cliquant avec le bouton droit sur le certificat, en cliquant sur ensuite **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Comment : afficher des certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Sécurisation des Services et Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
