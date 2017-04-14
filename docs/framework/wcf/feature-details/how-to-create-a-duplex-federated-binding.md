---
title: "Comment&#160;: cr&#233;er une liaison f&#233;d&#233;r&#233;e duplex | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Comment&#160;: cr&#233;er une liaison f&#233;d&#233;r&#233;e duplex
<xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande\/message de réponse.Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée.Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP.L'exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.  
  
 Vous pouvez également créer la liaison dans le code.Pour obtenir la description de la pile d'éléments de liaison à créer, consultez [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### Pour créer une liaison personnalisée fédérée duplex avec HTTP  
  
1.  Dans le nœud [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un élément [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Dans l’élément [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md), créez un élément [\<liaison\>](../../../../docs/framework/misc/binding.md) dont l'attribut `name` a la valeur `FederationDuplexHttpMessageSecurityBinding`.  
  
3.  Dans l’élément [\<liaison\>](../../../../docs/framework/misc/binding.md), créez un élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) dont l'attribut `authenticationMode` a la valeur `SecureConversation`.  
  
4.  Dans l’élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dont l'attribut `authenticationMode` a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5.  Après l'élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vide.  
  
6.  Après l'élément [\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md), créez un élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vide.  
  
7.  Après l'élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md), créez un élément [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vide.  
  
### Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP  
  
1.  Dans le nœud [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) du fichier de configuration, créez un élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md).  
  
2.  Dans l’élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md), créez un élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) dont l'attribut `name` a la valeur `FederationDuplexTcpMessageSecurityBinding`.  
  
3.  Dans l’élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md), créez un élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) dont l'attribut `authenticationMode` a la valeur `SecureConversation`.  
  
4.  Dans l’élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dont l'attribut `authenticationMode` a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5.  Après l'élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.  
  
### Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP  
  
1.  Dans le nœud [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) du fichier de configuration, créez un élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md).  
  
2.  Dans l’élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md), créez un élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) dont l'attribut `name` a la valeur `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3.  Dans l’élément [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md), créez un élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) dont l'attribut `authenticationMode` a la valeur `SecureConversation`.  
  
4.  Dans l’élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) dont l'attribut `authenticationMode` a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5.  Après l'élément [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md), créez un élément [\<sslStreamSecurity\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vide.  
  
6.  Après l'élément [\<sslStreamSecurity\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), créez un élément [\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.  
  
## Exemple de code  
  
#### Exemple avec 3 liaisons  
  
1.  Insérez le code suivant dans votre fichier de configuration.  
  
## Exemple  
  
```  
  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
  
```