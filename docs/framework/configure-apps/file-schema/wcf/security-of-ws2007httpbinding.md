---
title: "&lt;security&gt; de &lt;ws2007HttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;security&gt; de &lt;ws2007HttpBinding&gt;
Représente les paramètres de sécurité utilisés avec l'élément [\<ws2007HttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`mode`|-   Facultatif.  Spécifie le type de sécurité appliqué.  La valeur par défaut est `Message`.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.|  
  
## Mode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|`None`|La sécurité est désactivée.|  
|`Transport`|La sécurité est fournie à l'aide de HTTPS.  Le service doit être configuré avec les certificats SSL.  Le message est entièrement sécurisé à l'aide du protocole HTTPS et le service est authentifié par le client à l'aide du certificat SSL du service.  L'authentification du client est contrôlée à l'aide de l'attribut `ClientCredentials` de l'élément [\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md).|  
|`Message`|La sécurité est fournie à l'aide de la sécurité des messages SOAP.  Par défaut, le corps SOAP est chiffré et signé.  Ce mode offre diverses fonctionnalités : déterminer si les informations d'identification du service sont disponibles pour le client hors bande, quelle est la suite algorithmique à utiliser et quel niveau de protection est à appliquer au corps du message via le <xref:System.ServiceModel.Security.SecurityMessageProperty>, entre autres.  L'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
|`TransportWithMessageCredential`|Dans ce mode, le protocole HTTPS garantit l'intégrité, la confidentialité et l'authentification du serveur, et la sécurité des messages SOAP garantit l'authentification du client.  Par défaut, l'authentification du client est exécutée une fois par session et les résultats d'authentification sont mis en cache pour la durée de la session.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|Définit les paramètres de sécurité de transport.  Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.  Ces paramètres sont appliqués uniquement lorsque le mode a la valeur Transport.|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|Définit les paramètres de sécurité pour le message.  Cet élément correspond au type <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.  Ces paramètres ne sont pas appliqués lorsque le mode a la valeur Transport.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ws2007HttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Liaison sécurisée pour les applications de transport HTTP.|  
  
## Notes  
 Cet élément est conçu pour interagir avec les services qui implémentent les spécifications WS\-\*.  La sécurité de transport de cette liaison correspond à Secure Sockets Layer \(SSL\) sur HTTP, c'est\-à\-dire à HTTPS.  
  
## Voir aussi  
 <xref:System.ServiceModel.WSHttpSecurity>   
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)