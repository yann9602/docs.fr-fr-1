---
title: "WSDL et stratégie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f502d24f98c9229d064be3de0e0edc081664dd03
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wsdl-and-policy"></a>WSDL et stratégie
Cette rubrique traite des détails d'implémentation de WS-Policy, WS-PolicyAttachment et WSDL 1.1 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], ainsi que des assertions WS-Policy et des extensions WSDL 1.1 supplémentaires introduites par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente les spécifications WS-Policy et WS-PolicyAttachment soumises à W3C avec les contraintes et clarifications décrites dans ce document.  
  
 Ce document utilise les préfixes et espaces de noms répertoriés dans le tableau suivant.  
  
|Préfixe|Espace de noms|  
|------------|---------------|  
|wsp (WS-Policy 1,2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|wsp (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|MSF|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Extensions WSDL1.1 WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les extensions WSDL1.1 suivantes pour décrire les spécifications de session de contrat.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:boolean, indique que cette opération initie une session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ; la valeur par défaut est `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:boolean, indique que cette opération met fin à une session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ; la valeur par défaut est `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:boolean, indique que ce contrat requiert l'établissement d'une session.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Uri de transport de liaison HTTP SOAP 1.x  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les URI suivants pour indiquer les transports à utiliser pour les éléments d'extension de liaison WSDL 1.1, SOAP 1.1 et SOAP 1.2.  
  
|Transport|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Canaux nommés|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Assertions de stratégie implémentées par WCF  
 Outre les assertions de stratégie introduites dans les spécifications des services Web (WS-*) et mentionnées dans d'autres sections de ce document, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente les assertions de stratégie suivantes.  
  
|Assertion de stratégie|Sujet de stratégie|Description|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Point de terminaison|Le point de terminaison utilise l'authentification de base HTTP.|  
|http:HttpDigestAuthentication|Point de terminaison|Le point de terminaison utilise l'authentification Digest HTTP.|  
|http:HttpNegotiateAuthentication|Point de terminaison|Le point de terminaison utilise l'authentification par négociation HTTP.|  
|http:HttpNtlmAuthentication|Point de terminaison|Le point de terminaison utilise l'authentification NTLM HTTP.|  
|msf:Streamed|Point de terminaison|Le point de terminaison utilise le tramage de message diffusé en continu. Cette assertion est utilisée avec le protocole de tramage de message fourni pour les transports tels que TCP et canaux nommés.|  
|msf:SslTransportSecurity|Point de terminaison|Le point de terminaison utilise la sécurité de couche transport (TLS) avec le tramage de message.|  
|msf:WindowsTransportSecurity|Point de terminaison|Le point de terminaison utilise la négociation SPNEGO (Security Provider Negotiation) avec le tramage de message.|  
|msmq:MsmqBestEffort|Point de terminaison|MSMQ avec garanties de meilleur effort.|  
|msmq:MsmqSession|Point de terminaison|MSMQ avec garanties de session.|  
|msmq:MsmqVolatile|Point de terminaison|MSMQ Volatile.|  
|msmq:Authenticated|Point de terminaison|L'authentification est utilisée avec le transport MSMQ.|  
|msmq:WindowsDomain|Point de terminaison|MSMQ utilise l'authentification de domaine Windows.|  
|cdp:CompositeDuplex|Point de terminaison|Le point de terminaison utilise deux connexions de transport réciproques distinctes pour les messages entrants et sortants.|  
|mssp:RsaToken|Imbriqué|Assertion de jeton de clé RSA. Cette spécification est en général satisfaite par une clé RSA sérialisée directement dans le cadre des informations de clés dans une signature d'approbation.|  
|mssp:SslContextToken|Imbriqué|Requiert l'utilisation d'un SecurityContextToken obtenu à l'aide du protocole de transfert TLS binaire avec WS-Trust. Les assertions imbriquées incluent : sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Imbriqué|Indique une spécification selon laquelle aucun message de demande de jeton de sécurité de demande (RST) [WS-Trust] à l'aide de la liaison Annulation [WS-Trust, WS-SC] ne doit être envoyé à l'émetteur d'un SecurityContextToken donné. Si cette assertion est présente, ces messages de demande ne doivent pas être envoyés à l'émetteur. Si cette assertion est absente, ces messages de demande peuvent être envoyés à l'émetteur.|  
|mssp:RequireClientCertificate|Imbriqué|Cet élément facultatif indique une spécification selon laquelle un certificat client doit être fourni dans le cadre du protocole TLSNEGO. Si cette assertion est présente, un certificat client doit être fourni. Si cette assertion est absente, aucun certificat client ne doit être fourni. Cette assertion ne doit pas être utilisée en dehors de mssp:SslContextToken.|  
  
## <a name="see-also"></a>Voir aussi  
 [Publication WSDL personnalisée](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Comment : exporter un fichier WSDL personnalisé](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Comment : importer un fichier WSDL personnalisé](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
