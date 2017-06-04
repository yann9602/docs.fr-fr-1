---
title: "Guide de l&#39;interop&#233;rabilit&#233; des protocoles de services Web | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Guide de l&#39;interop&#233;rabilit&#233; des protocoles de services Web
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implémente plusieurs protocoles de services Web.  Un grand nombre de ces protocoles incluent plusieurs options et points d'extensibilité qui sont laissés à la discrétion de l'implémenteur.  Cette rubrique fournit une liste des protocoles des services Web implémentés par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  Des détails d'implémentation pour chaque protocole pris en charge sont fournis dans les autres rubriques de cette section.  
  
## Protocoles des services Web implémentés par WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une prise en charge des protocoles de l'infrastructure des services Web par l'intermédiaire des canaux, et des protocoles d'application de services Web par l'intermédiaire de la fonctionnalité de contrats.  L'interopérabilité pour les protocoles d'application s'effectue à l'aide des langages XSD \(XML Schema Description\) 1.0 et WSDL \(Web Services Description Language \) 1.1.  
  
 L'interopérabilité des protocoles d'infrastructure est fournie par la famille des spécifications WS\-\*.  Les canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assurent la prise en charge de plusieurs protocoles d'infrastructure WS\-\*.  Les canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont configurés à l'aide d'éléments de liaison.  Les tableaux suivants contiennent la liste complète des protocoles d'infrastructure WS\-\* implémentés par différents éléments de liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> prend en charge les spécifications présentées dans le tableau suivant :  
  
|Spécification\/document|Link|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|Liaison HTTP SOAP 1.1|[Protocole SOAP \(Simple Object Access Protocol\) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), Section 7|  
|Liaison HTTP SOAP 1,2|[SOAP Version 1.2, partie 2 : compléments \(deuxième édition\)](http://go.microsoft.com/fwlink/?LinkId=95329), Section 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> prennent en charge les spécifications présentées dans le tableau suivant :  
  
|Spécification\/Document|Link|  
|-----------------------------|----------|  
|XML|[Langage XML \(Extensible Markup Language\) 1.0 \(quatrième édition\)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1,1|[Protocole SOAP \(Simple Object Access Protocol\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Core|[SOAP Version 1.2, partie 1 : infrastructure de messagerie \(deuxième édition\)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS\-Addressing 2004\/08|[Web Services Addressing \(WS\-Addressing\)](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|W3C Web Services Addressing 1.0 – Éléments principaux|[Web Services Addressing 1.0 \- Éléments principaux](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|W3C Web Services Addressing 1.0 – Liaison SOAP|[Web Services Addressing 1.0 \- Liaison SOAP](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web Services Addressing 1.0 – Liaison WSDL\*|[Web Services Addressing 1.0 \- Liaison WSDL](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|W3C Web Services Addressing 1.0 \- Métadonnées|[Web Services Addressing 1.0 \- Métadonnées](http://www.w3.org/TR/ws-addr-metadata/)|  
|Liaison WSDL SOAP 1.1|[Langage WSDL \(Web Services Description Language\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|Liaison WSDL SOAP 1.2|[Extension de liaison WSDL 1.1 pour SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> prend en charge les spécifications présentées dans le tableau suivant :  
  
|Spécification\/document|Link|  
|-----------------------------|----------|  
|XOP|[XML\-binary Optimized Packaging](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|Liaison MTOM \+ SOAP1.2|[Mécanisme d'optimisation de la transmission des messages SOAP](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|Liaison MTOM SOAP 1.1|[Liaison SOAP 1.1 pour MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS\-PolicyAssertions|Résultats à publier.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> prend en charge les spécifications présentées dans le tableau suivant :  
  
|Spécification\/document|Link|  
|-----------------------------|----------|  
|WSS : SOAP Message Security 1,0|[Web Services Security : SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS : Username Token Profile 1.0|[Web Services Security UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> requérir Password\/@Type\=PasswordText \(valeur par défaut\)|  
|WSS : X.509 Token Profile 1.0|[Web Services Security X.509 Certificate Token Profile](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 Token Profile 1,0|[Web Services Security: SAML Token Profile](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS : SOAP Message Security 1.1|[Web Services Security : SOAP Message Security 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS Username Token Profile 1.1|[Web Services Security UsernameToken Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> n'implémentez pas la dérivation de clés basée sur mot de passe ;<br /><br /> requérir Password\/@Type\=PasswordText \(valeur par défaut\)|  
|WSS : X509 Token Profile 1.1|[Web Services Security X.509 Certificate Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Kerberos Token Profile 1.1|[Web Services Security Kerberos Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 Token Profile 1.1|[Web Services Security SAML Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS\-Secure Conversation|[Web Services Secure Conversation Language](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS\-Trust 1.4 \(page pouvant être en anglais\)|[Web Services Trust Language](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS\-SecurityPolicy 2005\/07|[Web Services Secure Conversation Language](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Selon les corrections des errata soumis au comité technique OASIS WS\-SX.<br /><br /> [ws\-sx message](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS\-ReliableMessaging 1.1|[Protocole de messagerie fiable version 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> prend en charge les spécifications présentées dans le tableau suivant :  
  
|Spécification\/Document|Link|  
|-----------------------------|----------|  
|WS\-Coordination|[Web Services Coordination](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS\-AtomicTransaction|[Web Services Atomic Transaction](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 Les classes  <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter> et <xref:System.ServiceModel.Description.MetadataResolver> fournissent la prise en charge des spécifications de métadonnées suivantes.  
  
-   [Schéma XML, partie 1 : structures \(deuxième édition\)](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [Schéma XML, partie 2 : types de données \(deuxième édition\)](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS\-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS\-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS\-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS\-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [WS\-Transfer Get pour la récupération de métadonnées](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 De plus, les profils d'interopérabilité suivants sont implémentés dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP Binding 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Basic Security Profile 1.0 document non définitif](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## Voir aussi  
 [Protocoles de services Web pris en charge par des liaisons d'interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)   
 [Protocoles de messagerie](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)   
 [Référence des schémas de contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [WSDL et stratégie](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)   
 [Protocoles de sécurité](../../../../docs/framework/wcf/feature-details/security-protocols.md)   
 [Protocole de messagerie fiable version 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)   
 [Protocole de messagerie fiable version 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)   
 [Protocoles de transaction](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)   
 [Protocole d'échange de contexte](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)