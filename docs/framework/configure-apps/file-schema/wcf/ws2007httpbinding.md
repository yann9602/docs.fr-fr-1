---
title: '&lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6af846937556968067d89a279e595374cce99ae4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt;
Définit une liaison interopérable qui assure la prise en charge des versions appropriées des éléments de liaison <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession> et <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.  
  
 \<system.serviceModel >  
\<liaisons >  
\<ws2007HttpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
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
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowCookies`|Valeur qui indique si le client accepte les cookies et les propage aux demandes suivantes. La valeur par défaut est `false`.<br /><br /> Vous pouvez utiliser cette propriété lors de l'interaction avec des services Web ASP.NET (ASMX) qui utilisent des cookies. Cela garantit que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|`bypassProxyOnLocal`|Valeur indiquant s'il faut ignorer le serveur proxy pour les adresses locales. La valeur par défaut est `false`.|  
|`closeTimeout`|Valeur <xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`hostnameComparisonMode`|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI (Uniform Resource Identifier). Cet attribut est de type <xref:System.ServiceModel.HostNameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI. La valeur par défaut est <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|`maxBufferPoolSize`|Taille maximale du pool de mémoires tampons pour cette liaison. La valeur par défaut est 524 288 octets (512 × 1 024). De nombreux éléments de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] utilisent des mémoires tampons. La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme le processus de garbage collection. Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la renvoyer dans le pool une fois que vous avez terminé. Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|`maxReceivedMessageSize`|Taille maximale du message (en octets), en-têtes compris, qu'un canal configuré avec cette liaison peut recevoir. L'expéditeur d'un message dépassant cette limite reçoit une erreur SOAP. Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi. La valeur par défaut est 65536.|  
|`messageEncoding`|Définit l'encodeur utilisé pour encoder le message. Les valeurs valides sont les suivantes :<br /><br /> -   `Text`: Utilisez un encodeur de message texte.<br />-   `Mtom`: Utilisez un encodeur Message Transmission Organization Mechanism 1.0 (MTOM).<br /><br /> La valeur par défaut est `Text`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nom de configuration de la liaison. Cette valeur doit être unique car elle permet d'identifier la liaison. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom. Pour plus d’informations sur la configuration par défaut et nommées liaisons et comportements, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`proxyAddress`|URI qui spécifie l'adresse du proxy HTTP. Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`. La valeur par défaut est `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi. Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>. La valeur par défaut est 00:01:00.|  
|`textEncoding`|Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison. Les valeurs valides sont les suivantes :<br /><br /> -   `UnicodeFffeTextEncoding`: Big Endian Unicode encodage.<br />-   `Utf16TextEncoding`: encodage 16 bits.<br />-   `Utf8TextEncoding`: encodage 8 bits.<br /><br /> La valeur par défaut est `Utf8TextEncoding`.<br /><br /> Cet attribut est de type <xref:System.Text.Encoding>.|  
|`transactionFlow`|Valeur indiquant si la liaison prend en charge le flux WS-Transactions. La valeur par défaut est `false`.|  
|`useDefaultWebProxy`|Valeur qui spécifie si le proxy HTTP du système configuré automatiquement est utilisé. La valeur par défaut est `true`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Définit les paramètres de sécurité de la liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Définit les contraintes de la complexité des messages SOAP que peuvent traiter les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Indique si des sessions fiables sont établies entre les points de terminaison de canal.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## <a name="remarks"></a>Remarques  
 `WS2007HttpBinding` ajoute une liaison fournie par le système semblable à `WSHttpBinding`, mais utilise les versions OASIS (Organization for the Advancement of Structured Information Standards) standard des protocoles ReliableSession, Security et TransactionFlow. Aucune modification du modèle objet ou des paramètres par défaut n’est requise en cas d’utilisation de cette liaison.  
  
## <a name="example"></a>Exemple  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<liaison >](../../../../../docs/framework/misc/binding.md)
