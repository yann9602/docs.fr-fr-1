---
title: Utilisation des certificats
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c38a697cc5f4693977e11ff71142322533e9ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-certificates"></a>Utilisation des certificats
Dans le cadre de la programmation de la sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], les certificats numériques X.509 sont fréquemment utilisés pour authentifier les clients et les serveurs, chiffrer les messages et signer numériquement ces derniers. Cette rubrique contient des explications sur les fonctionnalités de certificat numérique X.509 ainsi que des instructions permettant de les utiliser dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Elle renvoie également à d'autres rubriques qui abordent plus en détail ces différents concepts ou contiennent des instructions permettant d'effectuer des tâches courantes à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des certificats.  
  
 En bref, un certificat numérique fait partie d’un *infrastructure à clé publique* (PKI), qui est un système de certificats numériques, d’autorités de certification et d’autres autorités d’immatriculation qui vérifient et authentifient la validité de chaque partie impliquée dans une transaction électronique via l’utilisation du chiffrement à clé publique. Une autorité de certification émet des certificats et de chaque certificat possède un ensemble de champs qui contiennent des données, tels que *sujet* (l’entité à laquelle le certificat est émis), dates de validité (lorsque le certificat est valid), l’émetteur (le entité qui a émis le certificat) et une clé publique. Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], chacune de ces propriétés est traitée comme une revendication <xref:System.IdentityModel.Claims.Claim>, chaque revendication étant divisée en deux types supplémentaires : identité et droits. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consultez des certificats X.509 [des certificats de clé publique X.509](http://go.microsoft.com/fwlink/?LinkId=209952) [!INCLUDE[crabout](../../../../includes/crabout-md.md)] revendications et l’autorisation dans WCF consultez [la gestion des revendications et autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’implémentation d’une infrastructure à clé publique, voir [Windows Server 2008 R2 - Services de certificats](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 La principale fonction d'un certificat consiste à authentifier l'identité du propriétaire du certificat auprès des autres parties. Un certificat contient la *clé publique* du propriétaire, tandis que le propriétaire conserve la clé privée. Les clés publiques peuvent être utilisées pour chiffrer les messages envoyés au propriétaire du certificat. Cependant, seul le propriétaire de la clé privée pourra déchiffrer ces messages.  
  
 Les certificats doivent être émis par une autorité de certification, c'est-à-dire le plus souvent par une partie tierce. Les domaines Windows intègrent une autorité de certification pouvant être utilisée afin d'émettre des certificats pour les ordinateurs figurant sur ces domaines.  
  
## <a name="viewing-certificates"></a>Affichage des certificats  
 Si vous souhaitez utiliser des certificats, vous devrez souvent les afficher et examiner leurs propriétés au préalable. Pour ce faire, il vous suffit d'utiliser l'outil enfichable MMC (Microsoft Management Console). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : afficher des certificats avec le composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Magasin de certificats  
 Les certificats sont stockés dans des magasins. Deux emplacements de magasin majeurs existent et sont divisés en sous-magasins. Si vous disposez des droits administrateur sur un ordinateur, vous pouvez afficher ces deux principaux magasins à l'aide de l'outil enfichable MMC. Dans le cas contraire, vous pouvez uniquement afficher le magasin de l'utilisateur en cours.  
  
-   **Le magasin de l’ordinateur local**. Ce magasin contient les certificats utilisés par les processus informatiques tels que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Utilisez cet emplacement pour y stocker les certificats qui authentifient les serveurs auprès des clients.  
  
-   **Le magasin de l’utilisateur actuel**. Les applications interactives stockent en principe les certificats à cet emplacement pour l'utilisateur en train d'utiliser l'ordinateur. Si vous créer des applications clientes, c'est également l'emplacement que vous utiliserez en principe pour stocker les certificats qui authentifient les utilisateurs auprès des services.  
  
 Ces deux magasins sont divisés en sous-magasins. Les plus importants d'entre eux lors de la programmation avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont notamment :  
  
-   **Autorités de Certification racine**. Vous pouvez utiliser les certificats stockés dans ce magasin pour créer une chaîne de certificats, dont l'origine remontera à un certificat d'autorité de certification figurant dans ce magasin.  
  
    > [!IMPORTANT]
    >  L'ordinateur local approuve de manière implicite tous les certificats figurant dans ce magasin, même si ces certificats n'émanent pas d'une autorité de certification tierce approuvée. C'est pourquoi ne stockez pas de certificats dans ce magasin, à moins qu'il ne s'agisse de certificats publiés par des émetteurs dans lesquels vous entièrement confiance et à moins d'avoir pleinement conscience des conséquences d'un tel stockage.  
  
-   **Personnel**. Ce magasin est utilisé pour stocker les certificats associés à l'utilisateur d'un ordinateur. Ce magasin est en principe utilisé pour stocker les certificats publiés par l'un des certificats d'autorité de certification stockés dans le magasin Autorités de certification racine approuvées. Les certificats stockés dans ce magasin peuvent également s'être auto-publiés et avoir été approuvés par une application.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]magasins de certificats, consultez [des magasins de certificats](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Sélection d'un magasin  
 La sélection d'un magasin pour y stocker un certificat dépend de la manière dont un client ou service s'exécutent ainsi que de l'instant où ils s'exécutent. Les règles générales suivantes s'appliquent :  
  
-   Si le service WCF est hébergé dans un service Windows, utilisez le **ordinateur local** stocker. Remarque : des droits administrateur sont requis pour pouvoir stocker les certificats dans le magasin de l'ordinateur local.  
  
-   Si le service ou le client est une application qui s’exécute sous un compte d’utilisateur, utilisez la **utilisateur actuel** stocker.  
  
### <a name="accessing-stores"></a>Accès aux magasins  
 Les magasins sont protégés par des listes de contrôle d'accès à l'instar des dossiers figurant sur un ordinateur. Lors de la création d'un service hébergé par les services Internet (IIS), le processus [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] s'exécute sous le compte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Ce compte doit avoir accès au magasin contenant les certificats utilisés par le service considéré. Chacun des principaux magasins est protégé par une liste d'accès par défaut, mais cette liste peut être modifiée. Si vous créez un rôle distinct pour l'accès à un magasin donné, vous devez accorder à ce rôle des droits d'accès. Pour savoir comment modifier la liste d’accès à l’aide de l’outil WinHttpCertConfig.exe, consultez [Comment : créer des certificats temporaires à utiliser pendant le développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]utilisation des certificats clients avec les services IIS, consultez [comment appeler un service Web à l’aide d’un certificat client pour l’authentification dans une application Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Chaîne d'approbation et autorités de certification  
 Les certificats sont créés selone une hiérarchie où chaque certificat individuel est lié à l'autorité de certification qui l'a émis. Ce lien renvoie au certificat de l'autorité de certification. Le certificat de l'autorité de certification renvoie ensuite à l'autorité de certification qui a émis le certificat de l'autorité de certification d'origine. Ce processus se répète jusqu'à ce que le certificat de l'autorité de certification racine soit atteint. Le certificat de l'autorité de certification racine est approuvé de manière inhérente.  
  
 Certificats numériques sont utilisés pour authentifier les entités reposant sur cette hiérarchie, également appelée un *chaîne d’approbation*. Vous pouvez afficher toutes chaînes de certificat à l’aide du composant logiciel enfichable MMC en double-cliquant sur n’importe quel certificat, puis en cliquant sur le **chemin d’accès du certificat** onglet [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l’importation des chaînes de certificats pour une autorité de Certification, consultez [Comment : spécifier la chaîne de certificats autorité utilisée pour vérifier les Signatures](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Le statut d'autorité racine approuvée peut être attribué à tout émetteur. Il suffit pour ce faire de placer le certificat de cet émetteur dans le magasin Autorités de certification racine approuvées.  
  
### <a name="disabling-chain-trust"></a>Désactivation des chaînes d'approbation  
 Lorsque vous créez un nouveau service, il est possible que vous utilisiez un certificat non émis par un certificat racine approuvé ou que le certificat émetteur lui-même ne figure pas dans le magasin Autorités de certification racine approuvées. Vous pouvez désactiver le mécanisme assurant la vérification de la chaîne d'approbation d'un certificat uniquement à des fins de développement. Pour ce faire, affectez à la propriété `CertificateValidationMode` `PeerTrust` ou `PeerOrChainTrust`. L'un et l'autre des modes ci-dessus permettent de spécifier que le certificat doit s'auto-publier (approbation homologue) ou faire partie d'une chaîne d'approbation. Vous pouvez définir la propriété de n'importe laquelle des classes suivantes.  
  
|Classe|Propriété|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Vous pouvez également définir la propriété à l'aide de la configuration. Les éléments suivants sont utilisés pour spécifier le mode de validation :  
  
-   [\<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Authentification personnalisée  
 La propriété `CertificateValidationMode` vous permet également de personnaliser les modalités d'authentification des certificats. Par défaut, le niveau a la valeur `ChainTrust`. Pour utiliser la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, vous devez également affecter à l'attribut `CustomCertificateValidatorType` l'assembly et le type utilisés pour valider le certificat. Pour créer un validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  
  
 Lorsque vous créez un authentificateur personnalisé, la méthode la plus importante à substituer correspond à la méthode <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>. Pour obtenir un exemple d’authentification personnalisée, consultez le [validateur de certificat X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) exemple. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Informations d’identification personnalisées et Validation des informations d’identification](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>Utilisation de l'outil Makecert.exe pour construire une chaîne de certificat  
 L'outil de création de certificat (Makecert.exe) crée des certificats X.509 ainsi que des paires de clés publique/privée. Vous pouvez enregistre les clés privées sur votre disque, puis les utiliser pour émettre et signer de nouveaux certificats, instaurant ainsi une hiérarchie de certificats sous forme de chaîne. Cet outil est conçu uniquement pour vous assister lors du développement des services et ne doit en aucun cas être utilisé pour créer des certificats devant être effectivement déployés. Lorsque vous développez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], effectuez les étapes suivantes afin de construire une chaîne d'approbation à l'aide de l'outil Makecert.exe.  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>Pour construire une chaîne d'approbation à l'aide de l'outil Makecert.exe  
  
1.  Créez un certificat d'autorité racine temporaire (auto-signé) à l'aide de l'outil MakeCert.exe. Enregistrez la clé privée sur le disque.  
  
2.  Utilisez ce nouveau certificat pour émettre un autre certificat contenant la clé publique.  
  
3.  Importez le certificat d'autorité racine dans le magasin Autorités de certification racine approuvées.  
  
4.  Pour obtenir des instructions, consultez [Comment : créer des certificats temporaires à utiliser pendant le développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Quel certificat utiliser ?  
 Parmi les questions les plus fréquemment posées concernant les certificats figurent notamment : quel certificat choisir et pourquoi ? La réponse à ces questions n'est pas la même que vous programmiez un service ou un client. Les informations ci-dessous contiennent des directives générales et n'offrent pas une réponse exhaustive à ces questions.  
  
### <a name="service-certificates"></a>Certificats de service  
 La principale tâche des certificats de service consiste à authentifier le serveur auprès des clients. Un des contrôles initiales lorsqu’un client s’authentifie un serveur consiste à comparer la valeur de la **sujet** champ à l’identificateur de ressource uniforme (URI) utilisé pour contacter le service : leurs noms DNS respectifs doivent correspondre. Par exemple, si l’URI du service est « http://www.contoso.com/endpoint/ » le **sujet** champ doit contenir la valeur « www.contoso.com ».  
  
 Remarque : ce champ peut contenir plusieurs valeurs, chacune préfixée par une initialisation spécifiant la valeur. Dans la plupart des cas, cette initialisation correspond à « CN », abréviation de « common name », en français « nom courant », par exemple, « CN = www.contoso.com ». Il est également possible pour le **sujet** champ soit vide, auquel cas la **Subject Alternative Name** champ peut contenir la **nom DNS** valeur.  
  
 Notez également la valeur de la **prévus** champ du certificat doit inclure une valeur appropriée, comme « Authentification serveur » ou « Authentification cliente ».  
  
### <a name="client-certificates"></a>Certificats de client  
 Les certificats de client ne sont en principe pas publiés par une autorité de certification tierce. Le magasin personnel de l'utilisateur en cours contient en principe des certificats qui y sont stockés par l'autorité racine, le rôle prévu étant « Authentification de client ». Le client peut utiliser ce genre de certificat lorsque l'authentification mutuelle requise.  
  
## <a name="online-revocation-and-offline-revocation"></a>Révocations en ligne et hors ligne  
  
### <a name="certificate-validity"></a>Validité des certificats  
 Chaque certificat est valide uniquement pour une période donnée, appelée la *période de validité*. La période de validité est définie par le **valide à partir du** et **valide jusqu’au** champs d’un certificat X.509. Au cours de l'authentification, le certificat est contrôlé afin de vérifier que sa période de validité n'est pas échue.  
  
### <a name="certificate-revocation-list"></a>Liste de révocation des certificats  
 L'autorité de certification peut à tout moment révoquer un certificat tant que sa période de validité n'est pas échue. Une telle révocation peut avoir lieu pour plusieurs raisons, notamment lorsque la clé privée du certificat est compromise.  
  
 En cas de révocation, toutes les chaînes descendant du certificat révoqué ne sont plus considérées comme valables et ne sont plus approuvées pendant les procédures d'authentification. Pour savoir quels certificats sont révoqués, chaque émetteur publie une heure et date-horodaté *liste de révocation de certificats* (CRL). Cette liste peut être consultée à l'aide des révocations en ligne ou hors connexion en affectant à la propriété `RevocationMode` ou `DefaultRevocationMode` de l'une des classes suivantes l'une des valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> : <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> et les classes <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. La valeur par défaut de toutes les propriétés est `Online`.  
  
 Vous pouvez également définir le mode de configuration à l’aide du `revocationMode` attribut des deux le [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (de la [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) et le [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (de la [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>Méthode SetCertificate  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez fréquemment spécifier le certificat ou l'ensemble de certificats que les services ou clients doivent utiliser pour authentifier, chiffrer ou signer numériquement les messages. Pour ce faire, il vous suffit de rédiger un programme à l'aide de la méthode `SetCertificate` des diverses classes représentant les certificats X.509. Les classes suivantes utilisent la méthode `SetCertificate` pour spécifier un certificat.  
  
|Classe|Méthode|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 La méthode `SetCertificate` désigne un emplacement de magasin et y stocke un type « trouver » (paramètre `x509FindType`) qui spécifie un champ de certificat et la valeur de ce champ. Par exemple, le code suivant crée un <xref:System.ServiceModel.ServiceHost> de l’instance et définit le certificat de service utilisé pour authentifier le service aux clients avec la `SetCertificate` (méthode).  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Plusieurs certificats ayant la même valeur  
 Un magasin peut contenir plusieurs certificats ayant le même nom de sujet. Cela signifie que si vous indiquez que la `x509FindType` est <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> ou <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>et plus d’un certificat a la même valeur, une exception est levée méthode becausethereisno permettant de distinguer le certificat est requis. Vous pouvez résoudre ce problème en affectant à `x509FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Le champ d'empreinte contient une valeur unique qui peut être utilisée afin de trouver un certificat particulier figurant dans un magasin. Cette solution présente cependant un inconvénient : si le certificat a été révoqué ou renouvelé, la méthode `SetCertificate` échouera, l'empreinte du certificat n'existant plus. Si le certificat n'est plus valable, l'authentification échouera également. Pour résoudre ce problème, vous pouvez affecter au paramètre `x590FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName>, puis spécifier le nom de l'émetteur. Si aucun émetteur n'est requis, vous pouvez également lui affecter l'une des autres valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType> telles que <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certificats dans la configuration  
 Vous pouvez également définir des certificats à l'aide de la configuration. Si vous créez un service, les informations d’identification, y compris des certificats, sont spécifiées sous la [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Lorsque vous programmez un client, les certificats sont spécifiés sous la [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mappage d'un certificat à un compte utilisateur  
 Les services IIS et Active Directory proposent une fonctionnalité qui permet de mapper un certificat à un compte utilisateur Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]la fonctionnalité, consultez [mappe les certificats à des comptes d’utilisateur](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide du mappage de Active Directory, voir [mappage de certificats Client avec le mappage du Service d’annuaire](http://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Lorsque cette fonctionnalité est activée, vous pouvez affecter à la propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> la valeur `true`. Dans la configuration, vous pouvez définir le `mapClientCertificateToWindowsAccount` attribut de la [ \<authentification >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) élément `true`, comme illustré dans le code suivant.  
  
```xml  
<serviceBehaviors>  
 <behavior name="MappingBehavior">  
  <serviceCredentials>  
   <clientCertificate>  
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />  
   </clientCertificate>  
  </serviceCredentials>  
 </behavior>  
</serviceBehaviors>  
```  
  
 Le mappage d'un certificat X.509 au jeton représentant le compte utilisateur Windows est considéré comme un rehaussement des droits de ce compte. Une fois mappé, le jeton Windows peut en effet être utilisé pour accéder à des ressources protégées. C'est pourquoi la stratégie de domaine spécifie que le certificat X.509 doit être conforme aux règles qu'elle contient avant de pouvoir être mappé. Le *SChannel* package de sécurité applique cette exigence.  
  
 Lorsque vous utilisez le [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou version ultérieure, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que le certificat se conforme à la stratégie de domaine avant d'être mappé à un compte Windows.  
  
 Dans la première version de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le mappage du certificat est effectué sans prendre en compte la stratégie de domaine. Par conséquent, avec d’anciennes applications habituées à s’exécuter sous la première mise en production, il est possible que le mappage échoue si la fonctionnalité de mappage est activée et si le certificat X.509 n’est pas conforme à la stratégie de domaine.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Sécurisation des Services et Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
