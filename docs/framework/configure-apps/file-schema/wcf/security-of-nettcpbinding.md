---
title: "&lt;security&gt; de &lt;netTcpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# &lt;security&gt; de &lt;netTcpBinding&gt;
Définit les paramètres de sécurité d'une liaison.  
  
## Syntaxe  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Facultatif.  Spécifie le type de sécurité appliqué.  Les valeurs autorisées sont présentées ci\-dessous.  La valeur par défaut est `Transport`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.|  
  
## Attribut Mode  
  
|Valeur|Description|  
|------------|-----------------|  
|None|La sécurité est désactivée.|  
|Transport|La sécurité de transport est fournie à l'aide du TLS sur le TCP ou SPNego.  Le service peut devoir être configuré avec les certificats SSL.  Il est possible de contrôler le niveau de protection avec ce mode.|  
|Message|La sécurité est fournie à l'aide de la sécurité des messages SOAP.  Par défaut, le corps SOAP est chiffré et signé.  Ce mode offre diverses fonctionnalités, telles que, si les informations d'identification du service sont disponibles pour le client hors bande, la suite algorithmique à utiliser et quel niveau de protection à appliquer au corps du message.  L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
|TransportWithMessageCredential|La sécurité de transport est associée à la sécurité de message.  La sécurité de transport est fournie par le TLS sur le TCP ou SPNego, et garantit l'intégrité, la confidentialité et l'authentification du serveur.  La sécurité des messages SOAP fournit l'authentification du client.  Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Définit les paramètres de sécurité pour le transport.  Cet élément est de type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Définit les paramètres de sécurité pour le message.  Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Élément de liaison du [\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## Notes  
 Chaque liaison standard fournit des paramètres pour le contrôle des conditions de sécurité de transfert.  Ces paramètres incluent généralement le mode de sécurité qui indique si la sécurité au niveau du message ou du transport est utilisée et le choix du type d'informations d'identification du client.  Selon le choix d'options présentées par ces paramètres, une pile de canaux est construite avec la sécurité appropriée.  
  
 Les liaisons fournies par le système par Windows Communication Foundation \(WCF\) constituent un ensemble conçu pour satisfaire aux impératifs de scénario les plus courants.  Chaque liaison permet la spécification des conditions de sécurité pour des scénarios spécifiques.  
  
 Cet élément de configuration fournit les caractéristiques de sécurité pour `netTcpBinding`.  Il s'agit d'une liaison sécurisée, fiable et optimisée, adaptée à la communication entre ordinateurs.  Par défaut, elle génère une pile de communication d'exécution prenant en charge le TCP pour la remise des messages, Windows Security pour l'authentification et la sécurité des messages, WS\-ReliableMessaging pour la fiabilité et l'encodage de messages binaires.  
  
## Voir aussi  
 <xref:System.ServiceModel.NetTcpSecurity>   
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)