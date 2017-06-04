---
title: "Comment&#160;: configurer une confirmation de signature | Microsoft Docs"
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
  - "confirmation de signature"
  - "WCF, sécurité"
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Comment&#160;: configurer une confirmation de signature
La *confirmation de signature* est un mécanisme permettant à un initiateur de message de s'assurer qu'une réponse reçue a été générée suite au message d'origine de l'expéditeur.La confirmation de signature est définie dans la spécification WS\-Security 1.1.Si un point de terminaison prend en charge WS\-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.  
  
 Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.La procédure repose sur les étapes de base indiquées dans [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### Pour activer la confirmation de signature dans le code  
  
1.  Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.  
  
2.  Créez une instance de la classe <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
3.  Affectez `true` à <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A>.  
  
4.  Ajoutez l'élément de sécurité à la collection de liaisons.  
  
5.  Créez une liaison personnalisée, tel que spécifié dans [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### Pour activer la confirmation de signature dans la configuration  
  
1.  Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.  
  
2.  Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.  
  
3.  Ajoutez un élément d'encodage approprié.L'exemple suivant ajoute un élément `<TextMessageEncoding>`.  
  
4.  Ajoutez un élément enfant `<security>` et affectez `true` à l'attribut `requireSignatureConfirmation`.  
  
5.  Facultatif.Pour activer la confirmation de signature pendant le démarrage, ajoutez un élément enfant [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) et affectez `true` à l'attribut `equireSignatureConfirmation`.  
  
6.  Ajoutez un élément de transport approprié.L'exemple suivant ajoute un [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) :  
  
    ```  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## Exemple  
 Le code suivant crée une instance de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et affecte `true` à la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A>.Notez que cet exemple n'utilise pas l'élément `<secureConversationBootstrap>` indiqué dans l'exemple précédent.Cet exemple présente la confirmation de signature lors de l'utilisation d'un jeton Windows \(protocole Kerberos\).Dans ce cas, la signature du client est retournée dans toutes les réponses du service et est confirmée par le client.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>   
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)