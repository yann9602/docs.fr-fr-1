---
title: "Utilisation des certificats | Microsoft Docs"
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
  - "certificats (WCF)"
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Utilisation des certificats
Dans le cadre de la programmation de la sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], les certificats numériques X.509 sont fréquemment utilisés pour authentifier les clients et les serveurs, chiffrer les messages et signer numériquement ces derniers.Cette rubrique contient des explications sur les fonctionnalités de certificat numérique X.509 ainsi que des instructions permettant de les utiliser dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Elle renvoie également à d'autres rubriques qui abordent plus en détail ces différents concepts ou contiennent des instructions permettant d'effectuer des tâches courantes à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des certificats.  
  
 En bref, les certificats numériques font partie de l'*infrastructure à clé publique* \(PKI\). Cette infrastructure est en fait un système qui se compose de certificats numériques, d'autorités de certification ainsi que d'autorités d'immatriculation, lesquelles vérifient et authentifient les informations d'identification des parties impliquées dans une transaction électronique en utilisant un chiffrement à clé publique.Les autorités de certification émettent des certificats contenant un ensemble de champs qui définissent notamment les informations suivantes : *sujet* \(entité pour laquelle le certificat est émis\), dates de validité \(date de validé du certificat\), émetteur \(entité qui a émis le certificat\) et clé publique.Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], chacune de ces propriétés est traitée comme une revendication <xref:System.IdentityModel.Claims.Claim>, chaque revendication étant divisée en deux types supplémentaires : identité et droits.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les certificats X.509, consultez [Certificats de la clé publique X.509](http://go.microsoft.com/fwlink/?LinkId=209952)[!INCLUDE[crabout](../../../../includes/crabout-md.md)] Revendications et autorisation dans WCF, consultez [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'implémentation d'une infrastructure à clé publique, consultez [Windows Server 2008 R2 \- Services de certificats](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 La principale fonction d'un certificat consiste à authentifier l'identité du propriétaire du certificat auprès des autres parties.Un certificat contient la *clé publique* du propriétaire, tandis que le propriétaire conserve la clé privée.Les clés publiques peuvent être utilisées pour chiffrer les messages envoyés au propriétaire du certificat.Cependant, seul le propriétaire de la clé privée pourra déchiffrer ces messages.  
  
 Les certificats doivent être émis par une autorité de certification, c'est\-à\-dire le plus souvent par une partie tierce.Les domaines Windows intègrent une autorité de certification pouvant être utilisée afin d'émettre des certificats pour les ordinateurs figurant sur ces domaines.  
  
## Affichage des certificats  
 Si vous souhaitez utiliser des certificats, vous devrez souvent les afficher et examiner leurs propriétés au préalable.Pour ce faire, il vous suffit d'utiliser l'outil enfichable MMC \(Microsoft Management Console\).[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## Magasin de certificats  
 Les certificats sont stockés dans des magasins.Deux emplacements de magasin majeurs existent et sont divisés en sous\-magasins.Si vous disposez des droits administrateur sur un ordinateur, vous pouvez afficher ces deux principaux magasins à l'aide de l'outil enfichable MMC.Dans le cas contraire, vous pouvez uniquement afficher le magasin de l'utilisateur en cours.  
  
-   **Magasin de l'ordinateur local**.Ce magasin contient les certificats utilisés par les processus informatiques tels que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].Utilisez cet emplacement pour y stocker les certificats qui authentifient les serveurs auprès des clients.  
  
-   **Magasin de l'utilisateur en cours**.Les applications interactives stockent en principe les certificats à cet emplacement pour l'utilisateur en train d'utiliser l'ordinateur.Si vous créer des applications clientes, c'est également l'emplacement que vous utiliserez en principe pour stocker les certificats qui authentifient les utilisateurs auprès des services.  
  
 Ces deux magasins sont divisés en sous\-magasins.Les plus importants d'entre eux lors de la programmation avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont notamment :  
  
-   **Autorités de certification racine approuvées**.Vous pouvez utiliser les certificats stockés dans ce magasin pour créer une chaîne de certificats, dont l'origine remontera à un certificat d'autorité de certification figurant dans ce magasin.  
  
    > [!IMPORTANT]
    >  L'ordinateur local approuve de manière implicite tous les certificats figurant dans ce magasin, même si ces certificats n'émanent pas d'une autorité de certification tierce approuvée.C'est pourquoi ne stockez pas de certificats dans ce magasin, à moins qu'il ne s'agisse de certificats publiés par des émetteurs dans lesquels vous entièrement confiance et à moins d'avoir pleinement conscience des conséquences d'un tel stockage.  
  
-   **Personnel**.Ce magasin est utilisé pour stocker les certificats associés à l'utilisateur d'un ordinateur.Ce magasin est en principe utilisé pour stocker les certificats publiés par l'un des certificats d'autorité de certification stockés dans le magasin Autorités de certification racine approuvées.Les certificats stockés dans ce magasin peuvent également s'être auto\-publiés et avoir été approuvés par une application.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les magasins de certificats, consultez [Magasins de certificats](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### Sélection d'un magasin  
 La sélection d'un magasin pour y stocker un certificat dépend de la manière dont un client ou service s'exécutent ainsi que de l'instant où ils s'exécutent.Les règles générales suivantes s'appliquent :  
  
-   Si le service WCF est hébergé dans un service Windows, utilisez le certificat **ordinateur local**.Remarque : des droits administrateur sont requis pour pouvoir stocker les certificats dans le magasin de l'ordinateur local.  
  
-   Si le service ou le client est intégré à une application qui s'exécute sous un compte d'utilisateur, utilisez alors le magasin de l'**utilisateur en cours**.  
  
### Accès aux magasins  
 Les magasins sont protégés par des listes de contrôle d'accès à l'instar des dossiers figurant sur un ordinateur.Lors de la création d'un service hébergé par les services Internet \(IIS\), le processus [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] s'exécute sous le compte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].Ce compte doit avoir accès au magasin contenant les certificats utilisés par le service considéré.Chacun des principaux magasins est protégé par une liste d'accès par défaut, mais cette liste peut être modifiée.Si vous créez un rôle distinct pour l'accès à un magasin donné, vous devez accorder à ce rôle des droits d'accès.Pour savoir comment modifier la liste d'accès en utilisant l'outil WinHttpCertConfig.exe, consultez [Comment : créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation des certificats clients avec les services IIS, consultez [Procédure : appeler un service Web à l'aide d'un certificat client pour l'authentification dans une application Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## Chaîne d'approbation et autorités de certification  
 Les certificats sont créés selone une hiérarchie où chaque certificat individuel est lié à l'autorité de certification qui l'a émis.Ce lien renvoie au certificat de l'autorité de certification.Le certificat de l'autorité de certification renvoie ensuite à l'autorité de certification qui a émis le certificat de l'autorité de certification d'origine.Ce processus se répète jusqu'à ce que le certificat de l'autorité de certification racine soit atteint.Le certificat de l'autorité de certification racine est approuvé de manière inhérente.  
  
 Les certificats numériques sont utilisés pour authentifier les entités reposant sur cette hiérarchie, également appelée une *chaîne d'approbation*.Vous pouvez afficher toutes chaînes de certificat à l'aide de l'outil enfichable MMC. Il vous suffit de cliquer sur le certificat de votre choix, puis de sélectionner l'onglet **Chemin de certificat**.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'importation de chaînes de certificats pour une autorité de certification, consultez [Comment : spécifier la chaîne de certificats d'autorité de certification utilisée pour vérifier des signatures](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Le statut d'autorité racine approuvée peut être attribué à tout émetteur. Il suffit pour ce faire de placer le certificat de cet émetteur dans le magasin Autorités de certification racine approuvées.  
  
### Désactivation des chaînes d'approbation  
 Lorsque vous créez un nouveau service, il est possible que vous utilisiez un certificat non émis par un certificat racine approuvé ou que le certificat émetteur lui\-même ne figure pas dans le magasin Autorités de certification racine approuvées.Vous pouvez désactiver le mécanisme assurant la vérification de la chaîne d'approbation d'un certificat uniquement à des fins de développement.Pour ce faire, affectez à la propriété `CertificateValidationMode``PeerTrust` ou `PeerOrChainTrust`.L'un et l'autre des modes ci\-dessus permettent de spécifier que le certificat doit s'auto\-publier \(approbation homologue\) ou faire partie d'une chaîne d'approbation.Vous pouvez définir la propriété de n'importe laquelle des classes suivantes.  
  
|Classe|Propriété|  
|------------|---------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=fullName>|  
  
 Vous pouvez également définir la propriété à l'aide de la configuration.Les éléments suivants sont utilisés pour spécifier le mode de validation :  
  
-   [\<authentification\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## Authentification personnalisée  
 La propriété `CertificateValidationMode` vous permet également de personnaliser les modalités d'authentification des certificats.Par défaut, le niveau a la valeur `ChainTrust`.Pour utiliser la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode>, vous devez également affecter à l'attribut `CustomCertificateValidatorType` l'assembly et le type utilisés pour valider le certificat.Pour créer un validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.  
  
 Lorsque vous créez un authentificateur personnalisé, la méthode la plus importante à substituer correspond à la méthode <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>.Pour obtenir un exemple d'authentification personnalisée, consultez [X.509 Certificate Validator](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md).[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Informations d'identification personnalisées et validation d'informations d'identification](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## Utilisation de l'outil Makecert.exe pour construire une chaîne de certificat  
 L'outil de création de certificat \(Makecert.exe\) crée des certificats X.509 ainsi que des paires de clés publique\/privée.Vous pouvez enregistre les clés privées sur votre disque, puis les utiliser pour émettre et signer de nouveaux certificats, instaurant ainsi une hiérarchie de certificats sous forme de chaîne.Cet outil est conçu uniquement pour vous assister lors du développement des services et ne doit en aucun cas être utilisé pour créer des certificats devant être effectivement déployés.Lorsque vous développez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], effectuez les étapes suivantes afin de construire une chaîne d'approbation à l'aide de l'outil Makecert.exe.  
  
#### Pour construire une chaîne d'approbation à l'aide de l'outil Makecert.exe  
  
1.  Créez un certificat d'autorité racine temporaire \(auto\-signé\) à l'aide de l'outil MakeCert.exe.Enregistrez la clé privée sur le disque.  
  
2.  Utilisez ce nouveau certificat pour émettre un autre certificat contenant la clé publique.  
  
3.  Importez le certificat d'autorité racine dans le magasin Autorités de certification racine approuvées.  
  
4.  Pour des instructions pas à pas, consultez [Comment : créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## Quel certificat utiliser ?  
 Parmi les questions les plus fréquemment posées concernant les certificats figurent notamment : quel certificat choisir et pourquoi ?La réponse à ces questions n'est pas la même que vous programmiez un service ou un client.Les informations ci\-dessous contiennent des directives générales et n'offrent pas une réponse exhaustive à ces questions.  
  
### Certificats de service  
 La principale tâche des certificats de service consiste à authentifier le serveur auprès des clients.Lorsqu'un client authentifie un serveur, il compare d'abord la valeur du champ **Objet** à celle de l'URI \(Uniform Resource Identifier, URI\) utilisé pour contacter le service : leurs noms DNS respectifs doivent être identiques.Par exemple, si l'URI du service est « http:\/\/www.contoso.com\/endpoint\/ », alors le champ **Sujet** doit contenir la valeur « www.contoso.com ».  
  
 Remarque : ce champ peut contenir plusieurs valeurs, chacune préfixée par une initialisation spécifiant la valeur.Dans la plupart des cas, cette initialisation correspond à « CN », abréviation de « common name », en français « nom courant », par exemple, « CN \= www.contoso.com ».Le champ **Sujet** peut également être vierge auquel cas le champ **Autre nom du sujet** peut contenir la valeur **Nom DNS**.  
  
 Remarque : la valeur du champ **Rôles prévus** du certificat doit contenir une valeur appropriée telle que « Authentification de serveur » ou « Authentification de client ».  
  
### Certificats de client  
 Les certificats de client ne sont en principe pas publiés par une autorité de certification tierce.Le magasin personnel de l'utilisateur en cours contient en principe des certificats qui y sont stockés par l'autorité racine, le rôle prévu étant « Authentification de client ».Le client peut utiliser ce genre de certificat lorsque l'authentification mutuelle requise.  
  
## Révocations en ligne et hors ligne  
  
### Validité des certificats  
 Chaque certificat est valable pendant une période de temps donnée appelée *période de validité*.Cette période est définie par les champs **Valide à partir du** et **Valide jusqu'au** d'un certificat X.509.Au cours de l'authentification, le certificat est contrôlé afin de vérifier que sa période de validité n'est pas échue.  
  
### Liste de révocation des certificats  
 L'autorité de certification peut à tout moment révoquer un certificat tant que sa période de validité n'est pas échue.Une telle révocation peut avoir lieu pour plusieurs raisons, notamment lorsque la clé privée du certificat est compromise.  
  
 En cas de révocation, toutes les chaînes descendant du certificat révoqué ne sont plus considérées comme valables et ne sont plus approuvées pendant les procédures d'authentification.Pour savoir quels certificats sont révoqués, chaque émetteur publie une *liste de révocation de certificats* horodatée.Cette liste peut être consultée à l'aide des révocations en ligne ou hors connexion en affectant à la propriété `RevocationMode` ou `DefaultRevocationMode` de l'une des classes suivantes l'une des valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> : <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> et les classes <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>.La valeur par défaut de toutes les propriétés est `Online`.  
  
 Vous pouvez également définir le mode dans la configuration à l'aide de l'attribut `revocationMode` de [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) \(de la section [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)\) et de [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) \(de la section [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)\).  
  
## Méthode SetCertificate  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez fréquemment spécifier le certificat ou l'ensemble de certificats que les services ou clients doivent utiliser pour authentifier, chiffrer ou signer numériquement les messages.Pour ce faire, il vous suffit de rédiger un programme à l'aide de la méthode `SetCertificate` des diverses classes représentant les certificats X.509.Les classes suivantes utilisent la méthode `SetCertificate` pour spécifier un certificat.  
  
|Classe|Méthode|  
|------------|-------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 La méthode `SetCertificate` désigne un emplacement de magasin et y stocke un type « trouver » \(paramètre `x509FindType`\) qui spécifie un champ de certificat et la valeur de ce champ.Par exemple, le code suivant crée une instance <xref:System.ServiceModel.ServiceHost> et définit le certificat de service utilisé pour authentifier le service auprès des clients à l'aide de la méthode `SetCertificate` .  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### Plusieurs certificats ayant la même valeur  
 Un magasin peut contenir plusieurs certificats ayant le même nom de sujet.Cela signifie que si vous spécifiez que `x509FindType` a la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType> ou <xref:System.Security.Cryptography.X509Certificates.X509FindType> et que plusieurs certificats ont la même valeur, une exception sera levée, `aucun` moyenne permettant de distinguer quel certificat doit être utilisé.Vous pouvez résoudre ce problème en affectant à `x509FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType>.Le champ d'empreinte contient une valeur unique qui peut être utilisée afin de trouver un certificat particulier figurant dans un magasin.Cette solution présente cependant un inconvénient : si le certificat a été révoqué ou renouvelé, la méthode `SetCertificate` échouera, l'empreinte du certificat n'existant plus.Si le certificat n'est plus valable, l'authentification échouera également.Pour résoudre ce problème, vous pouvez affecter au paramètre `x590FindType` la valeur <xref:System.Security.Cryptography.X509Certificates.X509FindType>, puis spécifier le nom de l'émetteur.Si aucun émetteur n'est requis, vous pouvez également lui affecter l'une des autres valeurs d'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType> telles que <xref:System.Security.Cryptography.X509Certificates.X509FindType>.  
  
## Certificats dans la configuration  
 Vous pouvez également définir des certificats à l'aide de la configuration.Si vous créez un service, les informations d'identification de même que les certificats, sont spécifiés sous [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md).Si vous programmez un client, les certificats sont spécifiés sous [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## Mappage d'un certificat à un compte utilisateur  
 Les services IIS et Active Directory proposent une fonctionnalité qui permet de mapper un certificat à un compte utilisateur Windows.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la fonctionnalité, consultez [Mappage des certificats aux comptes d'utilisateurs](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation du mappage Active Directory, consultez [Mappage des certificats client à l'aide du mappage du service d'annuaire](http://go.microsoft.com/fwlink/?LinkId=88918) \(page pouvant être en anglais\).  
  
 Lorsque cette fonctionnalité est activée, vous pouvez affecter à la propriété <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> de la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> la valeur `true`.Dans la configuration, vous pouvez affecter à l'attribut `mapClientCertificateToWindowsAccount` de l'élément [\<authentification\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) la valeur `true`, comme illustré dans le code suivant.  
  
```  
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
  
 Le mappage d'un certificat X.509 au jeton représentant le compte utilisateur Windows est considéré comme un rehaussement des droits de ce compte. Une fois mappé, le jeton Windows peut en effet être utilisé pour accéder à des ressources protégées.C'est pourquoi la stratégie de domaine spécifie que le certificat X.509 doit être conforme aux règles qu'elle contient avant de pouvoir être mappé.Le package de sécurité *SChannel* intègre cette spécification.  
  
 Lorsque vous utilisez le [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou version ultérieure, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que le certificat se conforme à la stratégie de domaine avant d'être mappé à un compte Windows.  
  
 Dans la première version de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le mappage du certificat est effectué sans prendre en compte la stratégie de domaine.Par conséquent, avec d'anciennes applications habituées à s'exécuter sous la première version, il est possible que le mappage échoue si la fonctionnalité de mappage est activée et si le certificat X.509 n'est pas conforme à la stratégie de domaine.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels>   
 <xref:System.ServiceModel.Security>   
 <xref:System.ServiceModel>   
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>   
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)