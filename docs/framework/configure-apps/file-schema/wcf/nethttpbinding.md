---
title: "&lt;netHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;netHttpBinding&gt;
Représente une liaison qu'un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] peut utiliser pour configurer et exposer les points de terminaison qui peuvent communiquer sur HTTP.  Lorsqu'elle est utilisée avec un contrat duplex, WebSocket est utilisé, sinon HTTP est utilisé.  
  
## Syntaxe  
  
```vb  
  
```  
  
```csharp  
  
<netHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Binary/Text/Mtom"  
       name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"      
            maxStringContentLength="Integer" />  
   </binding>  
</netHttpBinding>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`allowCookies`|Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.  La valeur par défaut est `false`.<br /><br /> Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.  De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|`bypassProxyOnLocal`|Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.  La valeur par défaut est `false`.<br /><br /> Une ressource Internet est locale si elle dispose d'une adresse locale.  Une adresse locale est une adresse sur le même ordinateur, le réseau local ou l'intranet et est identifiée, syntaxiquement, par l'absence de point \(.\) comme dans les URI "http:\/\/webserver\/" et "http:\/\/localhost".<br /><br /> La définition de cet attribut détermine si les points de terminaison configurés avec le BasicHttpBinding utilisent le serveur proxy lors de l'accès aux ressources locales.  Si cet attribut est `true`, les demandes adressées à des ressources Internet locales n'utilisent pas le serveur proxy.  Utilisez le nom d'hôte \(plutôt que localhost\) si vous souhaitez que les clients traversent un proxy lorsqu'ils parlent aux services sur le même ordinateur et que cet attribut a la valeur `true`.<br /><br /> Si cet attribut est `false`, toutes les demandes Internet sont exécutées par le serveur proxy.|  
|`closeTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`hostnameComparisonMode`|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.  Cet attribut est de type <xref:System.ServiceModel.HostnameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.  La valeur par défaut est <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|`maxBufferPoolSize`|Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire de tampons des messages qui reçoivent des messages du canal.  La valeur par défaut est de 524 288 \(0x80000\) octets.<br /><br /> Le gestionnaire de tampons réduit le coût d'utilisation des mémoires tampons à l'aide d'un pool de mémoires tampons.  Les mémoires tampons sont requises par le service pour traiter des messages lorsqu'ils sortent du canal.  S'il n'y a pas mémoire suffisante dans le pool de mémoires tampons pour traiter la charge de message, le gestionnaire de mémoires tampons doit allouer de la mémoire additionnelle dans le segment de mémoire CLR, ce qui augmente le traitement de la garbage collection.  Une allocation importante de mémoire issue du tas de garbage CLR indique que la taille du pool de mémoires tampons est insuffisante et qu'il est possible d'améliorer les performances en augmentant la limite spécifiée par cet attribut.|  
|`maxBufferSize`|Entier qui spécifie la taille maximale, en octets, d'une mémoire tampon qui stocke des messages pendant qu'ils sont traités pour un point de terminaison configuré avec cette liaison.  La valeur par défaut est de 65 536 octets.|  
|`maxReceivedMessageSize`|Entier positif qui définit la taille maximale du message, en octets, y compris les en\-têtes d'un message pouvant être reçu sur un canal configuré avec cette liaison.  L'expéditeur reçoit une erreur SOAP si le message est trop grand pour le récepteur.  Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.  La valeur par défaut est 65 536 octets.|  
|`messageEncoding`|Définit l'encodeur utilisé pour encoder le message SOAP.  Les valeurs valides sont les suivantes :<br /><br /> -   Text : utiliser un encodeur de message texte.<br />-   Mtom : utiliser un encodeur Message Transmission Organization Mechanism 1.0 \(MTOM\).<br /><br /> La valeur par défaut est Text.  Cet attribut est de type <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Chaîne qui contient le nom de configuration de la liaison.  Cette valeur doit être unique car elle permet d'identifier la liaison.  Chaque liaison porte un `name` et a un attribut `namespace` qui l'identifient de façon unique dans les métadonnées du service.  De plus, ce nom est unique parmi les liaisons du même type.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Spécifie l'espace de noms XML de la liaison.  La valeur par défaut est « http:\/\/tempuri.org\/Bindings ».  Chaque liaison porte un `name` et a un attribut `namespace` qui l'identifient de façon unique dans les métadonnées du service.|  
|`openTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`proxyAddress`|URI qui contient l'adresse du proxy HTTP.  Si `useSystemWebProxy` a la valeur `true` ce paramètre doit avoir la valeur `null`.  La valeur par défaut est `null`.|  
|`receiveTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|`textEncoding`|Définit l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   BigEndianUnicode : encodage Unicode BigEndian.<br />-   Unicode : encodage 16 bits.<br />-   UTF8 : encodage 8 bits<br /><br /> La valeur par défaut est UTF8.  Cet attribut est de type <xref:System.Text.Encoding>.|  
|`transferMode`|Valeur <xref:System.ServiceModel.TransferMode> valide qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu dans une demande ou une réponse.|  
|`useDefaultWebProxy`|Valeur booléenne qui spécifie si le proxy HTTP du système, configuré automatiquement, doit être utilisé, le cas échéant.  La valeur par défaut est `true`.|  
|||  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Définit les paramètres de sécurité de la liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.NetHttpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## Notes  
 Le NetHttpBinding utilise HTTP en guise de transport pour envoyer des messages.  Lorsqu'elle est utilisée avec un contrat duplex, WebSocket est utilisé.  Lorsqu'elle est utilisée avec un contrat de demande\-réponse, NetHttpBinding se comporte comme un BasicHttpBinding avec un encodeur binaire.  
  
 La sécurité est désactivée par défaut, mais peut être ajoutée en affectant à l'attribut de mode de l'élément enfant [\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) une valeur autre que `None`.  Par défaut, il utilise un encodage de message "Texte" et un encodage texte UTF\-8.  
  
## Exemple  
 L'exemple suivant montre l'utilisation de <xref:System.ServiceModel.NetHttpBinding> qui fournit la communication HTTP et l'interopérabilité maximale avec les services Web de première et seconde génération.  La liaison est spécifiée dans les fichiers de configuration pour le client et le service.  Le type de liaison est spécifié à l'aide de l'attribut `binding` de l'élément `<endpoint>`.  Si vous souhaitez configurer la liaison de base et modifier certains de ses paramètres, vous devez définir une configuration de liaison.  Le point de terminaison doit référencer la configuration de liaison par nom en utilisant l'attribut `bindingConfiguration` de l'élément `<endpoint>`, comme présenté dans le code de configuration suivant pour le service.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## Exemple  
 Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Les fonctionnalités de l'exemple précédent peuvent être obtenues en supprimant le bindingConfiguration de l'adresse du point de terminaison et le nom de la liaison.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.Binding>   
 <xref:System.ServiceModel.Channels.BindingElement>   
 <xref:System.ServiceModel.BasicHttpBinding>   
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)