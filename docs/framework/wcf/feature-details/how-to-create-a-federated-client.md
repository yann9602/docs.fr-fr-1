---
title: "Comment&#160;: cr&#233;er un client f&#233;d&#233;r&#233; | Microsoft Docs"
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
  - "fédération"
  - "WCF, fédération"
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# Comment&#160;: cr&#233;er un client f&#233;d&#233;r&#233;
Dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], la création d'un client pour un *service fédéré* se compose de trois étapes principales :  
  
1.  Configurer un [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou une liaison personnalisée similaire.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'une liaison appropriée, consultez [Comment : créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).Ou bien, exécutez le [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) par rapport au point de terminaison de métadonnées du service fédéré pour générer un fichier de configuration pour communiquer avec le service fédéré et un ou plusieurs services d'émission de jeton de sécurité.  
  
2.  Définissez les propriétés du <xref:System.ServiceModel.Security.IssuedTokenClientCredential> qui contrôle différents aspects de l'interaction d'un client avec un service d'émission de jeton de sécurité.  
  
3.  Définissez les propriétés du <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> qui permet aux certificats nécessaires de communiquer en toute sécurité avec les points de terminaison donnés, tels que les services d'émission de jeton de sécurité.  
  
> [!NOTE]
>  Un <xref:System.Security.Cryptography.CryptographicException> peut être levé lorsqu'un client utilise des informations d'identification personnalisées, la liaison <xref:System.ServiceModel.WSFederationHttpBinding> ou un jeton émis de façon personnalisée, et des clés asymétriques.Les clés asymétriques sont utilisées avec la liaison <xref:System.ServiceModel.WSFederationHttpBinding> et les jetons émis de façon personnalisée lorsque les propriétés <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> et <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A>, respectivement, ont la valeur <xref:System.IdentityModel.Tokens.SecurityKeyType>.L'exception <xref:System.Security.Cryptography.CryptographicException> est levée lorsque le client tente d'envoyer un message et un profil utilisateur n'existe pas pour l'identité que le client emprunte.Pour minimiser ce problème, connectez\-vous à l'ordinateur client ou appelez `LoadUserProfile` avant d'envoyer le message.  
  
 Cette rubrique fournit des informations détaillées à propos de ces procédures.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'une liaison appropriée, consultez [Comment : créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le fonctionnement d'un service fédéré, consultez [Fédération](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### Pour générer et examiner la configuration d'un service fédéré  
  
1.  Exécutez le [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec l'adresse de l'URL de métadonnées du service comme un paramètre de ligne de commande.  
  
2.  Ouvrez le fichier de configuration généré dans un éditeur approprié.  
  
3.  Examinez les attributs et le contenu des éléments générés [\<issuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) et [\<issuerMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md).Ceux\-ci se trouvent à l'intérieur des éléments [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) pour le [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou les éléments de liaisons personnalisés.Vérifiez que les adresses contiennent les noms de domaine attendus ou d'autres informations d'adresse.Il est important de vérifier ces informations parce que le client authentifie auprès de ces adresses et peut divulguer des informations, telles que les paires de nom d'utilisateur\/mot de passe.Si l'adresse n'est pas l'adresse attendue, cela peut entraîner la divulgation d'informations à un destinataire involontaire.  
  
4.  Examinez tous les éléments [\<issuedTokenParameters\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) supplémentaires à l'intérieur de l'élément \<`alternativeIssuedTokenParameters`\> commenté.Lors de l'utilisation de l'outil Svcutil.exe pour générer la configuration pou un service fédéré, si le service fédéré ou tous les services d'émission de jeton de sécurité intermédiaires ne spécifient pas une adresse d'émetteur, mais spécifie une adresse de métadonnées pour un service d'émission de jeton de sécurité qui expose plusieurs points de terminaison, le fichier de configuration résultant fait référence au premier point de terminaison.Les points de terminaison supplémentaires sont dans le fichier de configuration comme éléments \<`alternativeIssuedTokenParameters`\> commentés.  
  
     Déterminez si l'un de ces \<`issuedTokenParameters`\> est préférable à celui déjà présent dans la configuration.Par exemple, le client peut choisir de s'authentifier auprès d'un service d'émission de jeton de sécurité à l'aide d'un jeton [!INCLUDE[infocard](../../../../includes/infocard-md.md)] Windows plutôt qu'une paire de nom d'utilisateur\/mot de passe.  
  
    > [!NOTE]
    >  Dans le cas où plusieurs services d'émission de jeton de sécurité doivent être parcourus avant de communiquer avec le service, il est possible pour un service d'émission de jeton de sécurité intermédiaire de diriger le client vers un service d'émission de jeton de sécurité incorrect.Par conséquent, vérifiez que le point de terminaison pour le service d'émission de jeton de sécurité dans le [\<issuedTokenParameters\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) est le service d'émission de jeton de sécurité attendu et pas un service d'émission de jeton de sécurité inconnu.  
  
### Pour configurer un IssuedTokenClientCredential dans le code  
  
1.  Accédez au <xref:System.ServiceModel.Security.IssuedTokenClientCredential> par le biais de la propriété <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> de la classe <xref:System.ServiceModel.Description.ClientCredentials> \(retournée par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601>, ou par le biais de la classe <xref:System.ServiceModel.ChannelFactory> \), comme s'affiché dans le code d'exemple suivant.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  Si la mise en cache de jeton n'est pas requise, affectez à la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> la valeur `false`.La propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> contrôle si les jetons d'un service d'émission de jeton de sécurité sont mis en cache.Si cette propriété a la valeur `false`, le client demande un nouveau jeton auprès du service d'émission de jeton de sécurité à chaque fois qu'il doit se  ré\-authentifier lui\-même auprès du service fédéré, qu'un jeton précédent soit encore valide ou non.Si cette propriété a la valeur `true`, le client réutilise un jeton existant toutes les fois qu'il doit se ré\-authentifier auprès du service fédéré \(tant que le jeton n'a pas expiré\).La valeur par défaut est `true`.  
  
3.  Si une limite de temps est requise sur les jetons mis en cache, affectez à la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> une valeur <xref:System.TimeSpan>.La propriété spécifie la durée de mise en cache d'un jeton.Au terme de l'intervalle de temps spécifié, le jeton est supprimé du cache client.Par défaut, les jetons sont mis en cache indéfiniment.L'exemple suivant affecte à l'intervalle de temps la valeur de 10 minutes.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  Facultatif.Affectez au <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> un pourcentage.La valeur par défaut est 60 \(pourcent\).La propriété spécifie un pourcentage de la période de validité du jeton.Par exemple, si le jeton émis est valide pour 10 heures et <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> a la valeur 80, le jeton est renouvelé après huit heures.L'exemple suivant affecte la valeur de 80 pourcent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     L'intervalle de renouvellement déterminé par la période de validité du jeton et la valeur `IssuedTokenRenewalThresholdPercentage` est substitué par la valeur `MaxIssuedTokenCachingTime` dans les cas où le temps de mise en cache est plus court que le temps du seuil de renouvellement.Par exemple, si le produit de `IssuedTokenRenewalThresholdPercentage` et la durée du jeton est huit heures, et la valeur `MaxIssuedTokenCachingTime` est 10 minutes, le client contacte le service d'émission de jeton de sécurité pour un jeton mis à jour toutes les 10 minutes.  
  
5.  Si un mode d'entropie de clé différent de <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> est exigé sur une liaison qui n'utilise pas la sécurité de message ou la sécurité de transport avec les informations d'identification de message \(par exemple,la liaison n'a pas de <xref:System.ServiceModel.Channels.SecurityBindingElement>\), affectez une valeur appropriée à la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A>.Le mode d'*entropie* détermine si les clés symétriques peuvent être contrôlées à l'aide de la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A>.Cette valeur par défaut est <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>, où le client et l'émetteur de jeton fournissent des données qui sont associées afin de produire la clé à part entière.D'autres valeurs sont <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> et <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>, ce qui signifie que la clé entière est spécifiée par le client ou le serveur, respectivement.L'exemple suivant définit la propriété afin d'utiliser uniquement les données de serveur pour la clé.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Si un <xref:System.ServiceModel.Channels.SecurityBindingElement> est présent dans un service d'émission de jeton de sécurité ou une liaison de service, le <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> défini sur <xref:System.ServiceModel.Security.IssuedTokenClientCredential> est substitué par la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> du `SecurityBindingElement`.  
  
6.  Configurez tout comportement de point de terminaison spécifique à l'émetteur en l'ajoutant à la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### Pour configurer IssuedTokenClientCredential dans la configuration  
  
1.  Créez un élément [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) comme un enfant de l'élément [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) dans un comportement de point de terminaison.  
  
2.  Si la mise en cache de jeton n'est pas requise, affectez à l'attribut `cacheIssuedTokens` \(de l'élément \<`issuedToken`\>\) la valeur `false`.  
  
3.  Si une limite de temps est requise sur les jetons mis en cache, affectez à l'attribut `maxIssuedTokenCachingTime` sur l'élément \<`issuedToken`\> une valeur appropriée.Par exemple :  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  Si une valeur différente de la valeur par défaut est souhaitée, affectez à l'attribut `issuedTokenRenewalThresholdPercentage` sur l'élément \<`issuedToken`\> une valeur appropriée, par exemple :  
  
    ```  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  Si un mode d'entropie de clé différente de `CombinedEntropy` est sur une liaison qui n'utilise pas la sécurité de message ou la sécurité de transport avec les informations d'identification de message \(par exemple, la liaison n'a pas de `SecurityBindingElement`\), attribuez à l'attribut `defaultKeyEntropyMode` sur l'élément `<issuedToken>` la valeur `ServerEntropy` ou `ClientEntropy` selon les besoins.  
  
    ```  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  Facultatif.Configurez tout comportement de point de terminaison personnalisé spécifique à l'émetteur en créant un élément \<`issuerChannelBehaviors`\> comme un enfant de l'élément \<`issuedToken`\>.Pour chaque comportement, créez un élément \<`add`\> comme un enfant de l'élément \<`issuerChannelBehaviors`\>.Spécifiez l'adresse de l'émetteur du comportement en définissant l'attribut `issuerAddress` sur l'élément \<`add`\>.Spécifiez le comportement lui\-même en définissant l'attribut `behaviorConfiguration` sur l'élément \<`add`\>.  
  
    ```  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### Pour configurer un X509CertificateRecipientClientCredential dans le code  
  
1.  Accédez à <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> par le biais de la propriété <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> de la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601> ou de la propriété <xref:System.ServiceModel.ChannelFactory>.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  Si une instance <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> est disponible pour le certificat pour un point de terminaison donné, utilisez la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A> de la collection retournée par la propriété <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  Si une instance <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> est non disponible, utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> comme indiqué dans l'exemple suivant.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### Pour configurer un X509CertificateRecipientClientCredential dans la configuration  
  
1.  Créez un élément [\<scopedCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) en tant qu'enfant de l'élément [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) lui\-même enfant de l'élément [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) dans un comportement de point de terminaison.  
  
2.  Créez un élément `<add>` en tant qu'enfant de l'élément `<scopedCertificates>`.Spécifiez des valeurs pour les attributs `storeLocation`, `storeName`, `x509FindType`et `findValue` pour faire référence au certificat approprié.Affectez à l'attribut `targetUri` une valeur qui fournit l'adresse du point de terminaison à laquelle le certificat est destiné, comme indiqué dans l'exemple suivant.  
  
    ```  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"   
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## Exemple  
 L'exemple de code suivant configure une instance de la classe <xref:System.ServiceModel.Security.IssuedTokenClientCredential> dans le code.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## Sécurité .NET Framework  
 Pour empêcher la divulgation d'informations possible, les clients qui exécutent l'outil Svcutil.exe pour traiter les métadonnées de points de terminaison fédérés doivent vérifier que les adresses de service d'émission de jeton de sécurité résultantes correspondent à celles qu'ils attendent.C'est particulièrement important lorsqu'un service d'émission de jeton de sécurité expose plusieurs points de terminaison, parce que l'outil Svcutil.exe génère le fichier de configuration résultant pour utiliser le premier tel point de terminaison, qui ne peut pas être celui le client doit utiliser.  
  
## LocalIssuer requis  
 Si les clients doivent toujours utiliser un émetteur local, prenez note des éléments suivants : la sortie par défaut de Svcutil.exe entraîne la non\-émission de l'émetteur local qui n'est pas utilisé si l'antépénultième service d'émission de jeton de sécurité dans la chaîne spécifie une adresse d'émetteur ou une adresse de métadonnées d'émetteur.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la définition des propriétés <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> et <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> de la classe <xref:System.ServiceModel.Security.IssuedTokenClientCredential>, consultez [Comment : configurer un émetteur local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## Certificats à étendue  
 Si les certificats de service doivent être spécifiés pour communiquer avec des services d'émission de jeton de sécurité, parce que la négociation de certificat n'est pas le plus souvent utilisée, ils peuvent être spécifiés à l'aide de la propriété <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>.La méthode <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> accepte un <xref:System.Uri> et un <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> comme paramètres.Le certificat spécifié est utilisé pour communiquer avec les points de terminaison à l'URI spécifié.Vous pouvez également utiliser la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> pour ajouter un certificat à la collection retournée par la propriété <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>.  
  
> [!NOTE]
>  L'idée cliente des certificats dont l'étendue englobe un URI donné s'applique uniquement à des applications qui effectuent des appels sortants aux services qui exposent des points de terminaison à ces URI.Elle ne s'applique pas aux certificats utilisés pour signer des jetons émis, tels que ceux configurés sur le serveur dans la collection retournée par le <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> de la classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## Voir aussi  
 [Federation, exemple](../../../../docs/framework/wcf/samples/federation-sample.md)   
 [Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)   
 [Comment : créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)   
 [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [Comment : configurer un émetteur local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [Considérations sur la sécurité des métadonnées](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)   
 [Comment : sécuriser des points de terminaison de métadonnées](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)