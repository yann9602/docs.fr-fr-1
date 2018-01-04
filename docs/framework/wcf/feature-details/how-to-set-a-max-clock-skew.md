---
title: "Comment : définir une inclinaison de l'horloge maximale"
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
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e186043a6cb32eaf5ed6bac6be3eaf50cb1ea32b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-max-clock-skew"></a>Comment : définir une inclinaison de l'horloge maximale
Les fonctions à durée critique peuvent dérailler si les paramètres de l'horloge sont différents sur deux ordinateurs. Pour limiter cette possibilité, vous pouvez affecter à la propriété `MaxClockSkew` un <xref:System.TimeSpan>. Cette propriété est disponible sur deux classes :  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Important pour une conversation sécurisée, des modifications à la `MaxClockSkew` propriété doit être effectuée lorsque le client ou le service est initialisé. Pour ce faire, vous devez définir la propriété sur le <xref:System.ServiceModel.Channels.SecurityBindingElement> retournée par le <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Pour modifier la propriété sur l'une des liaisons fournies par le système, vous devez rechercher l'élément de liaison de sécurité dans la collection de liaisons et affecter une nouvelle valeur à la propriété `MaxClockSkew`. Deux classes dérivent de <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Lorsque vous récupérez la liaison de sécurité de la collection, vous devez effectuer une conversion de type en l'un de ces types afin de définir correctement la propriété `MaxClockSkew`. L'exemple suivant utilise un <xref:System.ServiceModel.WSHttpBinding>, qui utilise <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Pour obtenir la liste qui spécifie le type de liaison de sécurité à utiliser dans chaque liaison fournie par le système, consultez [les liaisons fournies](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Pour créer une liaison personnalisée avec une nouvelle valeur d’inclinaison de l’horloge dans du code  
  
1.  > [!WARNING]
    >  Remarque Ajoutez des références aux espaces de noms suivants dans votre code : <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, et <xref:System.ServiceModel.Security.Tokens>.  
  
     Créez une instance d'une classe <xref:System.ServiceModel.WSHttpBinding> et choisissez le mode de sécurité <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Créez une nouvelle instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> en appelant la méthode <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.  
  
3.  Utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> pour rechercher l'élément de liaison de sécurité.  
  
4.  Lorsque vous utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>, effectuez une conversion de type au type réel. L'exemple suivant effectue une conversion de type au type <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
5.  Définissez la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> sur l'élément de liaison de sécurité.  
  
6.  Créez un <xref:System.ServiceModel.ServiceHost> avec un type de service approprié et une adresse de base.  
  
7.  Utilisez la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> pour ajouter un point de terminaison et inclure la <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Pour définir MaxClockSkew dans la configuration  
  
1.  Créer un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) dans les [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section de l’élément.  
  
2.  Créer un [ \<liaison >](../../../../docs/framework/misc/binding.md) et affectez le `name` attribut une valeur appropriée. L'exemple suivant lui affecte la valeur `MaxClockSkewBinding`.  
  
3.  Ajoutez un élément d'encodage. L’exemple ci-dessous ajoute un [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Ajouter un [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) et affectez le `authenticationMode` d’attribut à un paramètre approprié. L'exemple suivant affecte à l'attribut la valeur `Kerberos` pour spécifier que le service utilise l'authentification Windows.  
  
5.  Ajouter un [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) et définir le `maxClockSkew` par une valeur sous la forme de `"##:##:##"`. L'exemple suivant lui attribue la valeur 7 minutes. Si vous le souhaitez, ajoutez un [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) et définir le `maxClockSkew` d’attribut à un paramètre approprié.  
  
6.  Ajoutez un élément de transport. L’exemple suivant utilise une [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Pour une conversation sécurisée, les paramètres de sécurité doivent se produire sur le programme d’amorçage dans le [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
