---
title: "Comment&#160;: cr&#233;er une information d&#39;identification de prise en charge | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une information d&#39;identification de prise en charge
Il est possible d'avoir un modèle de sécurité personnalisé qui requiert plusieurs informations d'identification.  Par exemple, un service peut exiger du client non seulement un nom d'utilisateur et un mot de passe, mais également une information d'identification qui prouve que le client a plus de 18 ans.  La deuxième information d'identification est une *information d'identification de prise en charge*.  Cette rubrique explique comment implémenter de telles informations d'identification sur un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!NOTE]
>  La spécification pour la prise en charge d'informations d'identification fait partie de la spécification WS\-SecurityPolicy.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Spécifications Web Services Security](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## Supporting Tokens  
 En bref, lorsque vous utilisez la sécurité de message, une *information d'identification principale* est toujours utilisée pour sécuriser le message \(par exemple, un certificat X.509 ou un ticket Kerberos\).  
  
 Telle que définie par la spécification, une liaison de sécurité utilise des *jetons* pour sécuriser l'échange de messages.  Un *jeton* est une représentation d'une information d'identification de sécurité.  
  
 La liaison de sécurité utilise un jeton principal identifié dans la stratégie de liaison de sécurité pour créer une signature.  Cette signature porte le nom de *signature de message*.  
  
 Des jetons supplémentaires peuvent être spécifiés afin d'augmenter les revendications fournies par le jeton associé à la signature de message.  
  
## Endossement, signature et chiffrement  
 Une information d'identification de prise en charge provoque la transmission d'un *jeton de prise en charge* à l'intérieur du message.  La spécification WS\-SecurityPolicy définit quatre façons de joindre un jeton de prise en charge au message, comme décrit dans le tableau suivant.  
  
|Objectif|Description|  
|--------------|-----------------|  
|Signé|Le jeton de prise en charge est inclus dans l'en\-tête de sécurité et est signé par la signature de message.|  
|Endossement|Un *jeton d'endossement* signe la signature du message.|  
|Signé et endossement|Les jetons d'endossement signés signent l'élément `ds:Signature` entier produit à partir de la signature de message et sont eux\-mêmes signés par cette signature de message ; autrement dit, les deux jetons \(le jeton utilisé pour la signature de message et le jeton d'endossement signé\) se signent l'un l'autre.|  
|Signé et chiffrement|Les jetons de prise en charge chiffrés et signés sont des jetons de prise en charge signés qui sont également chiffrés lorsqu'ils apparaissent dans le `wsse:SecurityHeader`.|  
  
## Programmation d'informations d'identification de prise en charge  
 Pour créer un service qui utilise des jetons de prise en charge, vous devez créer un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).\)  
  
 La première étape de création d'une liaison personnalisée consiste à créer un élément de liaison de sécurité, qui peut être l'un des trois types suivants :  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Toutes les classes héritent de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement>, qui inclut quatre propriétés pertinentes :  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### Étendues  
 Il existe deux étendues pour les informations d'identification de prise en charge :  
  
-   Les *jetons de prise en charge de point de terminaison* prennent en charge toutes les opérations d'un point de terminaison.  Autrement dit, l'information d'identification que le jeton de prise en charge représente peut être utilisée chaque fois qu'une opération de point de terminaison est appelée.  
  
-   Les *jetons de prise en charge d'opération* prennent en charge uniquement une opération de point de terminaison spécifique.  
  
 Comme indiqué par les noms de propriétés, les informations d'identification de prise en charge peuvent être obligatoires ou facultatives.  Autrement dit, l'information d'identification de prise en charge est utilisée si elle est présente, bien que cela ne soit pas nécessaire, mais l'authentification n'échouera pas si elle n'est pas présente.  
  
## Procédures  
  
#### Pour créer une liaison personnalisée qui inclut des informations d'identification de prise en charge  
  
1.  Créez un élément de liaison de sécurité.  L'exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> avec le mode d'authentification `UserNameForCertificate`.  Utilisez la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2.  Ajoutez le paramètre de prise en charge à la collection de types retournée par la propriété appropriée \(`Endorsing`, `Signed`, `SignedEncrypted` ou `SignedEndorsed`\).  Les types dans l'espace de noms <xref:System.ServiceModel.Security.Tokens> incluent des types couramment utilisés, tels que <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## Exemple  
  
### Description  
 L'exemple suivant crée une instance du <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et ajoute une instance de la classe <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> à la collection retournée par la propriété Endorsing.  
  
### Code  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## Voir aussi  
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)