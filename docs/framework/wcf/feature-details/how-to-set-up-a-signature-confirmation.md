---
title: "Comment : configurer une confirmation de signature"
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
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53e38658671f3a36da67619c796667ecad61f286
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Comment : configurer une confirmation de signature
*Confirmation de signature* est un mécanisme pour un initiateur de message pour vous assurer qu’un message reçu a été généré en réponse au message d’origine de l’expéditeur. La confirmation de signature est définie dans la spécification WS-Security 1.1. Si un point de terminaison prend en charge WS-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.  
  
 Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. La procédure s’appuie sur les étapes de base trouvés dans [Comment : créer un personnalisé de liaison à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>Pour activer la confirmation de signature dans le code  
  
1.  Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.  
  
2.  Créez une instance de la <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.  
  
3.  Affectez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à `true`.  
  
4.  Ajoutez l’élément de sécurité à la collection de liaisons.  
  
5.  Créer une liaison personnalisée, comme spécifié dans [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>Pour activer la confirmation de signature dans la configuration  
  
1.  Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.  
  
2.  Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.  
  
3.  Ajoutez un élément d'encodage approprié. L'exemple suivant ajoute un élément `<TextMessageEncoding>`.  
  
4.  Ajoutez un élément enfant `<security>` et affectez `requireSignatureConfirmation` à l'attribut `true`.  
  
5.  Facultatif. Pour activer la confirmation de signature pendant le programme d’amorçage, ajoutez un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant et définissez la `equireSignatureConfirmation` attribut `true`.  
  
6.  Ajoutez un élément de transport approprié. L’exemple suivant ajoute une [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
    ```xml  
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
  
## <a name="example"></a>Exemple  
 Le code suivant crée une instance de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et affecte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à la propriété `true`. Notez que cet exemple n'utilise pas l'élément `<secureConversationBootstrap>` indiqué dans l'exemple précédent. Cet exemple présente la confirmation de signature lors de l'utilisation d'un jeton Windows (protocole Kerberos). Dans ce cas, la signature du client est retournée dans toutes les réponses du service et est confirmée par le client.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Guide pratique pour créer un SecurityBindingElement pour un mode d’authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
