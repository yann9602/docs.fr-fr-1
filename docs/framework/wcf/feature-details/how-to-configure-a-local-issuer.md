---
title: "Comment&#160;: configurer un &#233;metteur local | Microsoft Docs"
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
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Comment&#160;: configurer un &#233;metteur local
Cette rubrique décrit comment configurer un client afin d'utiliser un émetteur local pour les jetons émis.  
  
 Lorsqu'un client communique avec un service fédéré, il arrive souvent que le service spécifie l'adresse du service d'émission de jeton de sécurité qui est attendue pour émettre le jeton que le client utilisera pour s'authentifier auprès du service fédéré.Dans certains cas, le client peut être configuré pour utiliser un *émetteur local*.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise un émetteur local dans les cas où l'adresse de l'émetteur d'une liaison fédérée est http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous ou `null`.Dans ce cas, vous devez configurer <xref:System.ServiceModel.Description.ClientCredentials> avec l'adresse de l'émetteur local et la liaison à utiliser pour communiquer avec celui\-ci.  
  
> [!NOTE]
>  Si la propriété <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> de la classe `ClientCredentials` a la valeur `true`, qu'une adresse d'émetteur local n'est pas spécifiée, et que l'adresse d'émetteur spécifiée par [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou une autre liaison fédérée est http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self, http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous ou `null`, alors l'émetteur [!INCLUDE[infocard](../../../../includes/infocard-md.md)] Windows est utilisé.  
  
### Pour configurer l'émetteur local dans le code  
  
1.  Créez une variable de type <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Affectez à la variable la valeur de l'instance retournée par la propriété <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> de la classe `ClientCredentials`.Cette instance est retournée par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> du client \(héritée de <xref:System.ServiceModel.ClientBase%601>\) ou la propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> de <xref:System.ServiceModel.ChannelFactory> :  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Affectez une nouvelle instance de <xref:System.ServiceModel.EndpointAddress> à la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, avec l'adresse de l'émetteur local comme argument au constructeur.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Ou bien, créez une instance <xref:System.Uri> comme argument au constructeur.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     Le paramètre `addressHeaders` est un tableau d'instances <xref:System.ServiceModel.Channels.AddressHeader>, tel qu'indiqué ci\-après.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Définissez la liaison de l'émetteur local à l'aide de la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  Facultatif.Ajoutez des comportements de point de terminaison configurés pour l'émetteur local en ajoutant ces comportements à la collection retournée par la propriété <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### Pour configurer l'émetteur local dans la configuration  
  
1.  Créez un élément [\<localIssuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) en tant qu'enfant de l'élément [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) lui\-même enfant de l'élément [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) dans un comportement de point de terminaison.  
  
2.  Affectez à l'attribut `address` l'adresse de l'émetteur local qui acceptera des demandes de jeton.  
  
3.  Affectez aux attributs `binding` et `bindingConfiguration` des valeurs référençant la liaison appropriée à utiliser lors de la communication avec le point de terminaison de l'émetteur local.  
  
4.  Facultatif.Définissez l'élément [\<identité\>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) en tant qu'enfant de l'élément \<`localIssuer`\> et spécifiez les informations d'identité de l'émetteur local.  
  
5.  Facultatif.Définissez l'élément [\<en\-têtes\>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) en tant qu'enfant de l'élément \<`localIssuer`\> et spécifiez les en\-têtes supplémentaires requis pour adresser correctement l'émetteur local.  
  
## Sécurité .NET Framework  
 Notez que si une liaison et une adresse d'émetteur sont spécifiées pour une liaison donnée, l'émetteur local n'est pas utilisé pour les points de terminaison qui utilisent cette liaison.Les clients qui prévoient d'utiliser systématiquement l'émetteur local doivent s'assurer de ne pas utiliser de liaison de ce type ou de modifier la liaison afin que l'adresse de l'émetteur soit `null`.  
  
## Voir aussi  
 [Comment : configurer des informations d'identification sur un service FS \(Federation Service\)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [Comment : créer un client fédéré](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [Comment : créer une liaison WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)