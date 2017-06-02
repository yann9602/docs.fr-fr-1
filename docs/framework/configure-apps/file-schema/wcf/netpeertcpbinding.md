---
title: "&lt;netPeerTcpBinding&gt; | Microsoft Docs"
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
  - "netPeerBinding (élément)"
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# &lt;netPeerTcpBinding&gt;
Définit une liaison pour la messagerie TCP spécifique au canal homologue.  
  
## Syntaxe  
  
```  
  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de fermeture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|listenIPAddress|Chaîne indiquant une adresse IP utilisée par le nœud homologue pour écouter les messages TCP.  La valeur par défaut est `null`.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale du pool de mémoires tampons pour cette liaison.  La valeur par défaut est 524 288 octets \(512 x 1024\).  De nombreuses parties de Windows Communication Foundation \(WCF\) utilisent des mémoires tampons.  La création et la destruction des mémoires tampons à chaque utilisation sont chères, tout comme leur nettoyage.  Avec les pools de mémoires tampons, vous pouvez prendre une mémoire tampon du pool, l'utiliser et la retourner au pool une fois que vous avez terminé.  Ainsi, la surcharge de la création et de la destruction des mémoires tampons est évitée.|  
|maxReceivedMessageSize|Entier positif qui spécifie la taille maximale du message, en octets, y compris les en\-têtes, pouvant être reçu sur un canal configuré avec cette liaison.  L'expéditeur d'un message qui dépasse cette limite se verra notifier une erreur SOAP.  Ce dernier abandonne le message et crée une entrée d'événement dans le journal de suivi.  La valeur par défaut est 65536.|  
|name|Chaîne qui contient le nom de configuration de la liaison.  Cette valeur doit être unique car elle permet d'identifier la liaison.  Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d'avoir un nom.  Pour plus d'informations sur la configuration par défaut, ainsi que sur les comportements et les liaisons sans nom, consultez [Configuration simplifiée](../../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'ouverture.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
|port|Entier indiquant le port d'interface réseau utilisé par cette liaison pour traiter les messages TCP du canal homologue.  Cette valeur doit être comprise entre <xref:System.Net.IPEndPoint.MinPort> et <xref:System.Net.IPEndPoint.MaxPort>.  La valeur par défaut est 0.|  
|receiveTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération de réception.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:10:00.|  
|sendTimeout|<xref:System.TimeSpan> qui spécifie l'intervalle de temps prévu pour la réalisation d'une opération d'envoi.  Cette valeur doit être supérieure ou égale à <xref:System.TimeSpan.Zero>.  La valeur par défaut est 00:01:00.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Spécifie un programme de résolution d'homologue utilisé par cette liaison pour résoudre un ID de maille d'homologues en adresses IP de point de terminaison de nœuds dans la maille d'homologues.|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|Définit les paramètres de sécurité pour le message.  Cet élément est de type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaisons\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cet élément conserve une collection de liaisons standard et personnalisées.|  
  
## Notes  
 Cette liaison assure la prise en charge de la création d'applications d'égal à égal ou entre plusieurs parties utilisant le transport d'homologue sur TCP.  Chaque nœud homologue peut héberger plusieurs canaux homologues définis avec ce type de liaison.  
  
## Exemple  
 L'exemple suivant montre l'utilisation de la liaison NetPeerTcpBinding, qui fournit la communication pluripartite à l'aide d'un canal homologue.  Pour un scénario détaillé de l'utilisation de cette liaison, consultez [Net Peer TCP](http://msdn.microsoft.com/fr-fr/31f4db66-edb2-40a6-b92a-14098e92acae).  
  
```  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.NetPeerTcpBinding>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)   
 [Net Peer TCP](http://msdn.microsoft.com/fr-fr/31f4db66-edb2-40a6-b92a-14098e92acae)   
 [Réseaux homologues](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)