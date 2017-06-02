---
title: "&lt;security&gt; de &lt;webHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;security&gt; de &lt;webHttpBinding&gt;
Spécifie les conditions de sécurité requises pour un point de terminaison configuré avec un élément wsHttpBinding \(voir [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)\).  
  
## Syntaxe  
  
```  
  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Indique si un point de terminaison utilise la sécurité au niveau du transport ou s'il n'utilise aucune sécurité.  La valeur par défaut est `None`.  Cet attribut est de type <xref:System.ServiceModel.WebHttpSecurityMode>.|  
  
## Mode, attribut  
  
|Valeur|Description|  
|------------|-----------------|  
|None|La sécurité est désactivée.|  
|Transport|La sécurité est fournie à l'aide de HTTPS.  Le service doit être configuré avec les certificats SSL.  Le message est entièrement sécurisé à l'aide du protocole HTTPS et le service est authentifié par le client à l'aide du certificat SSL du service.  L'authentification du client est contrôlée via l'attribut `ClientCredentialType` du [\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).|  
|TransportCredentialOnly|Ce mode n'assure pas l'intégrité et la confidentialité des messages.  Il fournit l'authentification du client basée sur le protocole HTTP.  Ce mode doit être utilisé avec précaution.  Il doit être utilisé dans les environnements où la sécurité de transport est fournie par d'autres moyens \(tels que IPSec\) et où seule l'authentification du client est fournie par l'infrastructure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|Définit les paramètres de sécurité de transport.  Cet élément correspond au type <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Élément de liaison utilisé pour configurer des points de terminaison pour les services Web [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] qui répondent aux requêtes HTTP au lieu des messages SOAP.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>   
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.WebHttpSecurity>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)   
 [Modèle de programmation HTTP Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)