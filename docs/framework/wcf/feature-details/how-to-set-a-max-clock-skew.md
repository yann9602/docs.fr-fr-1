---
title: "Comment&#160;: d&#233;finir une inclinaison de l&#39;horloge maximale | Microsoft Docs"
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
  - "MaxClockSkew (propriété)"
  - "WCF, liaisons personnalisées"
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;finir une inclinaison de l&#39;horloge maximale
Les fonctions à durée critique peuvent dérailler si les paramètres de l'horloge sont différents sur deux ordinateurs.  Pour limiter cette possibilité, vous pouvez affecter à la propriété `MaxClockSkew` un <xref:System.TimeSpan>.  Cette propriété est disponible sur deux classes :  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Important   Pour une conversation sécurisée, les modifications de la propriété `MaxClockSkew` doivent être effectuées lorsque le service ou le client est initialisé.  Pour ce faire, vous devez affecter à la propriété la valeur de l'<xref:System.ServiceModel.Channels.SecurityBindingElement> retourné par <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Pour modifier la propriété sur l'une des liaisons fournies par le système, vous devez rechercher l'élément de liaison de sécurité dans la collection de liaisons et affecter une nouvelle valeur à la propriété `MaxClockSkew`.  Deux classes dérivent de <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.  Lorsque vous récupérez la liaison de sécurité de la collection, vous devez effectuer une conversion de type en l'un de ces types afin de définir correctement la propriété `MaxClockSkew`.  L'exemple suivant utilise un <xref:System.ServiceModel.WSHttpBinding>, qui utilise <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  Pour obtenir une liste qui spécifie quel type de liaison de sécurité utiliser dans chaque liaison fournie par le système, consultez [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### Pour créer une liaison personnalisée avec une nouvelle valeur d'inclinaison de l'horloge dans du code  
  
1.  > [!WARNING]
    >  Remarque   Ajoutez des références aux espaces de noms suivants dans votre code : <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions> et <xref:System.ServiceModel.Security.Tokens>.  
  
     Créez une instance d'une classe <xref:System.ServiceModel.WSHttpBinding> et choisissez le mode de sécurité <xref:System.ServiceModel.SecurityMode>.  
  
2.  Créez une nouvelle instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> en appelant la méthode <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.  
  
3.  Utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> pour rechercher l'élément de liaison de sécurité.  
  
4.  Lorsque vous utilisez la méthode <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>, effectuez une conversion de type au type réel.  L'exemple suivant effectue une conversion de type au type <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
5.  Définissez la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> sur l'élément de liaison de sécurité.  
  
6.  Créez un <xref:System.ServiceModel.ServiceHost> avec un type de service approprié et une adresse de base.  
  
7.  Utilisez la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> pour ajouter un point de terminaison et inclure la <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### Pour définir MaxClockSkew dans la configuration  
  
1.  Créez un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) dans la section de l'élément [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md).  
  
2.  Créez un élément [\<liaison\>](../../../../docs/framework/misc/binding.md) et affectez à l'attribut `name` une valeur adéquate.  L'exemple suivant lui affecte la valeur `MaxClockSkewBinding`.  
  
3.  Ajoutez un élément d'encodage.  L'exemple ci\-dessous ajoute un [\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Ajoutez un élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) et affectez un paramètre approprié à l'attribut `authenticationMode`.  L'exemple suivant affecte à l'attribut la valeur `Kerberos` pour spécifier que le service utilise l'authentification Windows.  
  
5.  Ajoutez un [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) et affectez à l'attribut `maxClockSkew` une valeur de la forme `"##:##:##"`.  L'exemple suivant lui attribue la valeur 7 minutes.  Ajoutez éventuellement un [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) et affectez un paramètre approprié à l'attribut `maxClockSkew`.  
  
6.  Ajoutez un élément de transport.  L'exemple ci\-dessous utilise un [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Pour une conversation sécurisée, les paramètres de sécurité doivent se produire à l'initialisation dans l'élément [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md).  
  
    ```  
  
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
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)