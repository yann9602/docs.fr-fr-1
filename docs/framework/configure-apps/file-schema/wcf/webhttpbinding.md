---
title: "&lt;webHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;webHttpBinding&gt;
Définit un élément de liaison utilisé pour configurer des points de terminaison pour les services Web [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] qui répondent aux requêtes HTTP au lieu de messages SOAP.  
  
## Syntaxe  
  
```  
  
<webHttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxBufferSize="integer"  
        maxReceivedMessageSize="Integer"  
        name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        useDefaultWebProxy="Boolean">  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        <security mode="None/Transport/TransportCredentialOnly">  
            <transport clientCredentialType =   
                 "Basic/Certificate/Digest/None/Ntlm/Windows"  
                  proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                  realm="string" />  
        </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</webHttpBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|allowCookies|Valeur booléenne qui indique si le client accepte les cookies et les propage dans de futures demandes.  La valeur par défaut est false.<br /><br /> Vous pouvez utiliser cette propriété lorsque vous interagissez avec les services Web ASMX qui utilisent des cookies.  De cette manière, vous avez la certitude que les cookies retournés par le serveur sont automatiquement copiés dans toutes les futures demandes du client pour ce service.|  
|bypassProxyOnLocal|Valeur booléenne qui indique s'il faut ignorer le serveur proxy pour les adresses locales.  La valeur par défaut est `false`.|  
|closeTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|hostnameComparisonMode|Spécifie le mode de comparaison du nom d'hôte HTTP utilisé pour analyser des URI.  Cet attribut est de type <xref:System.ServiceModel.HostnameComparisonMode>, ce qui indique si le nom d'hôte est utilisé pour atteindre le service en cas de correspondance sur l'URI.  La valeur par défaut est <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, qui ignore le nom d'hôte dans la correspondance.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.  La valeur par défaut est 524 288 octets \(512 x 1024\).  De nombreuses parties de Windows Communication Foundation \(WCF\) utilisent des mémoires tampons.  La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.  Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.  Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|maxBufferSize|Entier qui spécifie la quantité de mémoire maximale allouée pour une utilisation par le gestionnaire des tampons de messages qui reçoivent des messages du canal.  La valeur par défaut est de 524 288 \(0x80000\) octets.|  
|maxReceivedMessageSize|Entier positif qui spécifie la taille maximale du message, en octets, y compris les en\-têtes, pouvant être reçu sur un canal configuré avec cette liaison.  L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur.  Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.  La valeur par défaut est 65536. **Note:**  L'augmentation de cette valeur uniquement n'est pas suffisant en mode compatible ASP.NET.  Vous devez aussi augmenter la valeur de `httpRuntime` \(consultez [httpRuntime, élément \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/e9b81350-8aaf-47cc-9843-5f7d0c59f369)\).|  
|name|Chaîne qui contient le nom de configuration de la liaison.  Cette valeur doit être unique car elle permet d'identifier la liaison.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|proxyAddress|URI qui spécifie l'adresse du proxy HTTP.  Si `useSystemWebProxy` est `true`, ce paramètre doit avoir la valeur `null`.  La valeur par défaut est `null`.|  
|receiveTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|sendTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|transferMode.|Valeur <xref:System.ServiceModel.TransferMode> qui indique si le service configuré avec les liaisons utilise des modes de transfert de messages en continu ou en mémoire tampon \(ou les deux\).  La valeur par défaut est `Buffered`.|  
|useDefaultWebProxy|Valeur booléenne qui spécifie si le proxy HTTP du système configuré automatiquement est utilisé.  La valeur par défaut est `true`.|  
|writeEncoding|Spécifie l'encodage de caractères utilisé pour le texte du message.  Les valeurs valides sont les suivantes :<br /><br /> UnicodeFffeTextEncoding : encodage Unicode Big Endian.<br /><br /> Utf16TextEncoding : encodage 16 bits.<br /><br /> Utf8TextEncoding : encodage 8 bits.<br /><br /> La valeur par défaut est Utf8TextEncoding.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes de la complexité des messages POX qui peuvent être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Définit les paramètres de sécurité de la liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## Notes  
 Le modèle de programmation du Web [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] permet aux développeurs d'exposer des services Web [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] à travers les requêtes HTTP qui utilisent la messagerie de style « XML de base » \(POX\) au lieu de la messagerie basée sur SOAP.  Pour que les clients communiquent avec un service à l'aide de requêtes HTTP, un point de terminaison du service doit être configuré avec le [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) auquel \<WebHttpBehavior\> est attaché.  
  
 Le support de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pour la syndication et l'intégration ASP.AJAX est construit au sommet du modèle de programmation Web.  Pour plus d'informations sur le modèle, consultez [Modèle de programmation HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 [Modèle de programmation HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)