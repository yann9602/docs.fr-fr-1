---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;informations d&#39;identification de client et de service personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;informations d&#39;identification de client et de service personnalis&#233;es
Cette rubrique indique comment implémenter des informations d'identification de client et de service personnalisées et comment les utiliser à partir du code d'application.  
  
## Classes d'extensibilité d'informations d'identification  
 Les classes <xref:System.ServiceModel.Description.ClientCredentials> et <xref:System.ServiceModel.Description.ServiceCredentials> sont les points d'entrée principaux à l'extensibilité de la sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Ces classes d'informations d'identification fournissent les API qui permettent au code d'application de définir des informations d'identification et de convertir les types d'informations d'identification en jetons de sécurité.\(Les *jetons de sécurité* constituent la forme utilisée pour transmettre des informations d'identification à l'intérieur des messages SOAP.\) Les responsabilités de ces classes d'informations d'identification peuvent être réparties en deux catégories :  
  
-   Fournir les API pour que les applications définissent des informations d'identification.  
  
-   S'exécuter en tant que fabrique pour les implémentations <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 Les deux classes <xref:System.ServiceModel.Description.ClientCredentials> et <xref:System.ServiceModel.Description.ServiceCredentials> héritent de la classe <xref:System.ServiceModel.Security.SecurityCredentialsManager> abstraite qui définit le contrat permettant de retourner <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les classes d'informations d'identification et la manière dont elles s'intègrent dans l'architecture de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Security Architecture](http://msdn.microsoft.com/fr-fr/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 Les implémentations par défaut fournies dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prennent en charge les types d'informations d'identification fournis par le système et créent un gestionnaire de jetons de sécurité capable de gérer ces types d'informations d'identification.  
  
## Raisons de la personnalisation  
 La personnalisation des classes d'informations d'identification de service ou de client peut se justifier pour plusieurs raisons.La plus importante est la nécessité de modifier le comportement de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par défaut concernant la gestion des types d'informations d'identification fournis par le système, en particulier pour les motifs suivants :  
  
-   Modifications qu'il n'est pas possible d'effectuer à l'aide d'autres points d'extensibilité.  
  
-   Ajout de nouveaux types d'informations d'identification.  
  
-   Ajout de nouveaux types de jetons de sécurité personnalisés.  
  
 Cette rubrique décrit comment implémenter des informations d'identification de client et de service personnalisées et comment les utiliser à partir du code d'application.  
  
## Première étape  
 La création d'une classe d'informations d'identification personnalisée n'est que la première étape, car la personnalisation des informations d'identification a pour objectif de modifier le comportement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] concernant la fourniture, la sérialisation de jeton de sécurité ou l'authentification des informations d'identification.D'autres rubriques de cette section décrivent comment créer des sérialiseurs et authentificateurs personnalisés.À cet égard, la création de la classe d'informations d'identification personnalisées constitue la première rubrique.Les actions suivantes \(création de sérialiseurs et authentificateurs personnalisés\) peuvent être effectuées uniquement après la création d'informations d'identification personnalisées.Les autres rubriques basées sur celles\-ci sont les suivantes :  
  
-   [Comment : créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Comment : créer un authentificateur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## Procédures  
  
#### Pour implémenter des informations d'identification de client personnalisées  
  
1.  Définissez une nouvelle classe dérivée de la classe <xref:System.ServiceModel.Description.ClientCredentials>.  
  
2.  Facultatif.Ajoutez de nouvelles propriétés ou méthodes pour les nouveaux types d'informations d'identification.Si vous n'ajoutez pas de nouveau type d'informations d'identification, ignorez cette étape.L'exemple suivant ajoute une propriété `CreditCardNumber`.  
  
3.  Substituez la méthode <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>.Cette méthode est automatiquement appelée par l'infrastructure de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de l'utilisation des informations d'identification de client personnalisées.Cette méthode est chargée de créer et de retourner une instance d'une implémentation de la classe <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
    > [!IMPORTANT]
    >  Il est important de noter que la méthode <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> est remplacée pour créer un gestionnaire de jetons de sécurité personnalisé.Le gestionnaire de jetons de sécurité, dérivé de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, doit retourner un fournisseur de jetons de sécurité personnalisé, dérivé de <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, pour créer le jeton de sécurité réel.Si vous ne suivez pas ce modèle pour créer des jetons de sécurité, votre application peut ne pas fonctionner correctement lorsque des objets <xref:System.ServiceModel.ChannelFactory> sont mis en cache \(comportement par défaut des proxys clients WCF\), ce qui peut éventuellement provoquer une attaque par élévation de privilège.L'objet personnalisé d'informations d'identification est mis en cache dans le cadre de <xref:System.ServiceModel.ChannelFactory>.Toutefois, le <xref:System.IdentityModel.Selectors.SecurityTokenManager> personnalisé est créé à chaque appel, ce qui limite la menace de sécurité dès l'instant où la logique de création de jeton est placée dans <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Substituez la méthode <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### Pour implémenter un gestionnaire de jetons de sécurité client personnalisé  
  
1.  Définissez une nouvelle classe dérivée de <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenProvider> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les fournisseurs de jetons de sécurité personnalisés, consultez [Comment : créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les authentificateurs de jetons de sécurité personnalisés, consultez [Comment : créer un authentificateur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les jetons de sécurité personnalisés et les sérialiseurs de jetons de sécurité personnalisés, consultez [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### Pour utiliser des informations d'identification de client personnalisées à partir du code de l'application  
  
1.  Créez une instance du client généré qui représente l'interface de service, ou créez une instance de <xref:System.ServiceModel.ChannelFactory> qui pointe vers un service avec lequel vous souhaitez communiquer.  
  
2.  Supprimez le comportement d'informations d'identification de client fourni par le système de la collection <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A>, qui est accessible via la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A>.  
  
3.  Créez une nouvelle instance d'une classe d'informations d'identification de client personnalisées et ajoutez\-la à la collection <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A>, qui est accessible via la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A>.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 La procédure précédente indique comment utiliser les informations d'identification du client à partir du code de l'application.Les informations d'identification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent également être configurées en utilisant le fichier de configuration de l'application.L'utilisation de la configuration de l'application est souvent préférable à l'encodage effectué de manière irréversible, car elle permet de modifier les paramètres d'application sans qu'il soit nécessaire de modifier la source, de recompiler et de redéployer.  
  
 La procédure suivante décrit comment assurer la prise en charge de la configuration des informations d'identification personnalisées.  
  
#### Création d'un gestionnaire de configuration pour les informations d'identification de client personnalisées  
  
1.  Définissez une nouvelle classe dérivée de <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  Facultatif.Ajoutez des propriétés pour tous les paramètres de configuration supplémentaires que vous souhaitez exposer via la configuration de l'application.L'exemple ci\-dessous ajoute une propriété appelée `CreditCardNumber`.  
  
3.  Substituez la propriété <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> pour retourner le type de la classe d'informations d'identification de client personnalisées créée avec l'élément de configuration.  
  
4.  Substituez la méthode <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A>.La méthode est chargée de créer et de retourner une instance de la classe d'informations d'identification personnalisées en fonction des paramètres chargés à partir du fichier de configuration.Appelez la méthode <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> de base à partir de cette méthode pour récupérer les paramètres d'informations d'identification fournis par le système chargés dans votre instance d'informations d'identification de client personnalisées.  
  
5.  Facultatif.Si vous avez ajouté des propriétés supplémentaires dans l'étape 2, vous devez substituer la propriété <xref:System.Configuration.ConfigurationElement.Properties%2A> pour enregistrer vos paramètres de configuration supplémentaires afin que l'infrastructure de configuration les reconnaisse.Combinez vos propriétés avec celle de la classe de base afin de permettre la configuration des paramètres fournis par le système via cet élément de configuration d'informations d'identification de client personnalisées.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Lorsque vous disposez de la classe de gestionnaire de configuration, vous pouvez l'intégrer dans l'infrastructure de configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Cela permet d'utiliser les informations d'identification de client personnalisées dans les éléments de comportement de point de terminaison client, tel qu'indiqué dans la procédure suivante.  
  
#### Pour inscrire et utiliser un gestionnaire de configuration d'informations d'identification de client personnalisées dans la configuration de l'application  
  
1.  Ajoutez un élément \<`extensions`\> et un élément \<`behaviorExtensions`\> au fichier de configuration.  
  
2.  Ajoutez un élément \<`add`\> à l'élément \<`behaviorExtensions`\> et affectez une valeur appropriée à l'attribut `name`.  
  
3.  Affectez le nom de type complet à l'attribut `type`.Incluez également le nom d'assembly ainsi que les autres attributs d'assembly.  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Après avoir inscrit votre gestionnaire de configuration, l'élément d'informations d'identification personnalisées peut être utilisé à l'intérieur du même fichier de configuration au lieu de l'élément \<`clientCredentials`\> fourni par le système.Vous pouvez utiliser à la fois les propriétés fournies par le système et les nouvelles propriétés ajoutées à votre implémentation de gestionnaire de configuration.L'exemple suivant définit la valeur d'une propriété personnalisée à l'aide de l'attribut `creditCardNumber`.  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### Pour implémenter des informations d'identification de service personnalisées  
  
1.  Définissez une nouvelle classe dérivée de <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  Facultatif.Ajoutez de nouvelles propriétés pour fournir des API aux nouvelles valeurs d'informations d'identification ajoutées.Si vous n'ajoutez pas de nouvelle valeur d'informations d'identification, ignorez cette étape.L'exemple suivant ajoute une propriété `AdditionalCertificate`.  
  
3.  Substituez la méthode <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>.Cette méthode est automatiquement appelée par l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de l'utilisation des informations d'identification de client personnalisées.La méthode est chargée de créer et de retourner une instance d'une implémentation de la classe <xref:System.IdentityModel.Selectors.SecurityTokenManager> \(décrite dans la procédure suivante\).  
  
4.  Facultatif.Substituez la méthode <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A>.Cela est uniquement requis lors de l'ajout de nouvelles propriétés ou de nouveaux champs internes à l'implémentation d'informations d'identification de client personnalisées.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### Pour implémenter un gestionnaire de jetons de sécurité de service personnalisé  
  
1.  Définissez une nouvelle classe dérivée de la classe <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>.  
  
2.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenProvider> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les fournisseurs de jetons de sécurité personnalisés, consultez [Comment : créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les authentificateurs de jetons de sécurité personnalisés, consultez la rubrique [Comment : créer un authentificateur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Facultatif.Substituez la méthode <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> si une implémentation <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> personnalisée doit être créée.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les jetons de sécurité personnalisés et les sérialiseurs de jetons de sécurité personnalisés, consultez [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### Pour utiliser des informations d'identification de service personnalisées à partir du code de l'application  
  
1.  Créez une instance de <xref:System.ServiceModel.ServiceHost>.  
  
2.  Supprimez le comportement d'informations d'identification de service fourni par le système de la collection <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>.  
  
3.  Créez une instance de la classe d'informations d'identification de service personnalisées et ajoutez\-la à la collection <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Ajoutez la prise en charge de la configuration à l'aide des étapes décrites précédemment dans les procédures « `To create a configuration handler for custom client credentials` » et « `To register and use a custom client credentials configuration handler in the application configuration` ». La seule différence réside dans l'utilisation de la classe <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> au lieu de la classe <xref:System.ServiceModel.Configuration.ClientCredentialsElement> comme classe de base pour le gestionnaire de configuration.L'élément d'informations d'identification de service personnalisées peut ensuite être utilisé partout où l'élément `<serviceCredentials>` fourni par le système est utilisé.  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ServiceCredentials>   
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>   
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>   
 [Comment : créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)   
 [Comment : créer un authentificateur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)   
 [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)