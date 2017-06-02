---
title: "&lt;ws2007FederationHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;ws2007FederationHttpBinding&gt;
Liaison sécurisée et interopérable qui dérive de [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) et prend en charge la sécurité fédérée.  
  
## Syntaxe  
  
```  
  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`bypassProxyOnLocal`|Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales.  La valeur par défaut est `false`.|  
|`closeTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`hostnameComparisonMode`|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.  Cet attribut est de type <xref:System.ServiceModel.HostnameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.  La valeur par défaut est <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|`maxBufferPoolSize`|Taille maximale du pool de mémoires tampons pour cette liaison.  La valeur par défaut est 524 288 octets \(512 x 1024\).  De nombreux éléments de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] utilisent des mémoires tampons.  La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.  Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.  Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|`maxReceivedMessageSize`|Taille maximale du message \(en octets\), en\-têtes compris, pouvant être reçu sur un canal configuré avec cette liaison.  L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.  Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.  La valeur par défaut est 65536.|  
|`messageEncoding`|Définit l'encodeur utilisé pour encoder le message.  Les valeurs valides sont les suivantes :<br /><br /> -   Text : utiliser un encodeur de message texte.<br />-   Mtom : utiliser un encodeur Message Transmission Organization Mechanism 1.0 \(MTOM\).<br /><br /> La valeur par défaut est Text.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nom de configuration de la liaison.  Cette valeur doit être unique car elle permet d'identifier la liaison.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`privactyNoticeAt`|URI d'emplacement de l'avis de confidentialité.|  
|`privactyNoticeVersion`|Numéro de version de l'avis de confidentialité.|  
|`proxyAddress`|URI qui spécifie l'adresse du proxy HTTP.  Si `useDefaultWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.  La valeur par défaut est `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`textEncoding`|Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   BigEndianUnicode : encodage Unicode Big Endian.<br />-   Unicode : encodage 16 bits.<br />-   UTF8 : encodage 8 bits.<br /><br /> La valeur par défaut est UTF8.  Cet attribut est de type <xref:System.Text.Encoding>.|  
|`transactionFlow`|Valeur indiquant si la liaison prend en charge le flux WS\-Transactions.  La valeur par défaut est `false`.|  
|`useDefaultWebProxy`|Valeur indiquant si le proxy HTTP du système configuré automatiquement est utilisé.  L'adresse proxy doit être `null` \(autrement dit, pas de jeu\) si cet attribut est `true`.  La valeur par défaut est `true`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Définit les paramètres de sécurité pour le message.  Cet élément est de type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Indique si des sessions fiables sont établies entre les points de terminaison de canal.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## Notes  
 La fédération est la capacité à partager des identités entre plusieurs entreprises ou domaines approuvés à des fins d'authentification et d'autorisation.  Elle utilise le protocole WS\-Trust pour mapper la représentation d'identité entre domaines approuvés.  Une liaison HTTP fédérée prend en charge la sécurité SOAP ainsi que la sécurité en mode mixte, mais pas la sécurité de transport.  Les services configurés avec cette liaison doivent utiliser le transport HTTP.  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
## Exemple  
  
```  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>   
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>   
 [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)