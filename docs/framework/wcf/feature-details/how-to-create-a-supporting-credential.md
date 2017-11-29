---
title: "Comment : créer une information d'identification de prise en charge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c140b96fab0227a1563c8c1a511053d8d1ab944
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-supporting-credential"></a>Comment : créer une information d'identification de prise en charge
Il est possible d'avoir un modèle de sécurité personnalisé qui requiert plusieurs informations d'identification. Par exemple, un service peut exiger du client non seulement un nom d'utilisateur et un mot de passe, mais également une information d'identification qui prouve que le client a plus de 18 ans. Les informations d’identification deuxième sont un *prise en charge des informations d’identification*. Cette rubrique explique comment implémenter de telles informations d'identification sur un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!NOTE]
>  La spécification pour la prise en charge d'informations d'identification fait partie de la spécification WS-SecurityPolicy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Spécifications web Services Security](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Supporting Tokens  
 En bref, lorsque vous utilisez la sécurité de message, un *les informations d’identification principale* est toujours utilisé pour sécuriser le message (par exemple, un certificat X.509 ou un ticket Kerberos).  
  
 Comme défini par la spécification, une liaison de sécurité utilise *jetons* pour sécuriser l’échange de messages. A *jeton* est une représentation d’une information d’identification de sécurité.  
  
 La liaison de sécurité utilise un jeton principal identifié dans la stratégie de liaison de sécurité pour créer une signature. Cette signature est appelée le *signature de message*.  
  
 Des jetons supplémentaires peuvent être spécifiés afin d'augmenter les revendications fournies par le jeton associé à la signature de message.  
  
## <a name="endorsing-signing-and-encrypting"></a>Endossement, signature et chiffrement  
 Les informations d’identification de prise en charge des résultats dans un *jeton de prise en charge* transmis à l’intérieur du message. La spécification WS-SecurityPolicy définit quatre façons de joindre un jeton de prise en charge au message, comme décrit dans le tableau suivant.  
  
|Objectif|Description|  
|-------------|-----------------|  
|Signé|Le jeton de prise en charge est inclus dans l'en-tête de sécurité et est signé par la signature de message.|  
|Endossement|Un *jeton d’endossement* signe la signature du message.|  
|Signé et endossement|Les jetons d'endossement signés signent l'élément `ds:Signature` entier produit à partir de la signature de message et sont eux-mêmes signés par cette signature de message ; autrement dit, les deux jetons (le jeton utilisé pour la signature de message et le jeton d'endossement signé) se signent l'un l'autre.|  
|Signé et chiffrement|Les jetons de prise en charge chiffrés et signés sont des jetons de prise en charge signés qui sont également chiffrés lorsqu'ils apparaissent dans le `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programmation d'informations d'identification de prise en charge  
 Pour créer un service qui utilise des jetons de prise en charge que vous devez créer un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 La première étape de création d’une liaison personnalisée consiste à créer un élément de liaison de sécurité, qui peut être l’un des trois types suivants :  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Toutes les classes héritent de l'objet <xref:System.ServiceModel.Channels.SecurityBindingElement>, qui inclut quatre propriétés pertinentes :  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Étendues  
 Il existe deux étendues pour les informations d'identification de prise en charge :  
  
-   *Point de terminaison prenant en charge les jetons* prend en charge toutes les opérations d’un point de terminaison. Autrement dit, l'information d'identification que le jeton de prise en charge représente peut être utilisée chaque fois qu'une opération de point de terminaison est appelée.  
  
-   *Opération prise en charge des jetons* prend en charge qu’une opération de point de terminaison spécifique.  
  
 Comme indiqué par les noms de propriétés, les informations d'identification de prise en charge peuvent être obligatoires ou facultatives. Autrement dit, l'information d'identification de prise en charge est utilisée si elle est présente, bien que cela ne soit pas nécessaire, mais l'authentification n'échouera pas si elle n'est pas présente.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Pour créer une liaison personnalisée qui inclut des informations d'identification de prise en charge  
  
1.  Créez un élément de liaison de sécurité. L'exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> avec le mode d'authentification `UserNameForCertificate`. Utilisez la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2.  Ajoutez le paramètre de prise en charge à la collection de types retournée par la propriété appropriée (`Endorsing`, `Signed`, `SignedEncrypted` ou `SignedEndorsed`). Les types dans l'espace de noms <xref:System.ServiceModel.Security.Tokens> incluent des types couramment utilisés, tels que <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple suivant crée une instance du <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et ajoute une instance de la classe <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> à la collection retournée par la propriété Endorsing.  
  
### <a name="code"></a>Code  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
