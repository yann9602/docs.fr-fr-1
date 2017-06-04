---
title: "&lt;wsHttpContextBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;wsHttpContextBinding&gt;
Fournit un contexte pour le <xref:System.ServiceModel.WsHttpBinding> qui requiert la signature du niveau de protection.  
  
## Syntaxe  
  
```  
  
<wsHttpContextBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
          contextProtectionLevel="EncryptAndSign/None/Sign"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                defaultRealm="string" />  
          <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</wsHttpContextBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|allowCookies|Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.  La valeur par défaut est `false`.<br /><br /> Lorsque `allowCookies` a la valeur `true`, contextChannel utilise httpCookies comme mode d'échange de contexte.  Lorsque cet attribut a la valeur `false`, le contexte est échangé comme en\-têtes SOAP.<br /><br /> La valeur par défaut est `false`.<br /><br /> Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.  De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|bypassProxyOnLocal|Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.  La valeur par défaut est `false`.|  
|closeTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|contextProtectionLevel|Valeur <xref:System.Net.Security.ProtectionLevel> valide indiquant le niveau de protection souhaité pour l'en\-tête SOAP qui est utilisé pour propager les informations de contexte.  La valeur par défaut est `Sign`.|  
|hostnameComparisonMode|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.  Cet attribut est de type <xref:System.ServiceModel.HostnameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.  La valeur par défaut est <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.  La valeur par défaut est 524 288 octets \(512 x 1024\).  De nombreuses parties de Windows Communication Foundation \(WCF\) utilisent des mémoires tampons.  La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.  Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.  Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|maxReceivedMessageSize|Entier positif qui spécifie la taille maximale du message, en octets, y compris les en\-têtes, pouvant être reçu sur un canal configuré avec cette liaison.  L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.  Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.  La valeur par défaut est 65536.|  
|messageEncoding|Définit l'encodeur utilisé pour encoder le message.  Les valeurs valides sont les suivantes :<br /><br /> -   Text : utiliser un encodeur de message texte.<br />-   Mtom : utiliser un encodeur Message Transmission Organization Mechanism 1.0 \(MTOM\).<br />-   La valeur par défaut est Text.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Chaîne qui contient le nom de configuration de la liaison.  Cette valeur doit être unique car elle permet d'identifier la liaison.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|proxyAddress|URI qui spécifie l'adresse du proxy HTTP.  Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.  La valeur par défaut est `null`.|  
|receiveTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|sendTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|textEncoding|Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   UnicodeFffeTextEncoding : encodage Unicode Big Endian.<br />-   Utf16TextEncoding : encodage 16 bits.<br />-   Utf8TextEncoding : encodage 8 bits.<br /><br /> La valeur par défaut est Utf8TextEncoding.<br /><br /> Cet attribut est de type <xref:System.Text.Encoding>.|  
|transactionFlow|Valeur booléenne qui spécifie si la liaison prend en charge le flux WS\-Transactions.  La valeur par défaut est `false`.|  
|useDefaultWebProxy|Valeur booléenne qui spécifie si le proxy HTTP du système configuré automatiquement est utilisé.  La valeur par défaut est `true`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Définit les paramètres de sécurité de la liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Spécifie si des sessions fiables sont établies entre les points de terminaison du canal.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## Voir aussi  
 <xref:System.ServiceModel.WSHttpBinding>   
 <xref:System.ServiceModel.WSHttpContextBinding>   
 <xref:System.ServiceModel.Configuration.wsHttpContextBindingElement>   
 <xref:System.ServiceModel.Channels.ContextBindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)   
 [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)