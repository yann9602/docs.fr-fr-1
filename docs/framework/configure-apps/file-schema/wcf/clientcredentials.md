---
title: "&lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt;
Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.  
  
## Syntaxe  
  
```  
  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`supportInteractive`|Valeur booléenne indiquant si un utilisateur interactif peut sélectionner les informations d'identification d'un client pendant l'exécution.  La valeur par défaut est `true`.|  
|`type`|Chaîne qui spécifie le type de cet élément de configuration.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Indique le certificat utilisé pour authentifier le client auprès du service.  Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest\>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Indique un message condensé utilisé pour authentifier le client auprès du service.  Cet élément est de type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Spécifie un type de jeton personnalisé utilisé pour authentifier le client à un service STS.  Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Spécifie des informations d'identification d'homologue actuelles.  Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Spécifie le certificat utilisé pour authentifier le service auprès du client et fournit une structure permettant de définir des options de certificat.  Ce certificat doit être fourni au client hors bande, à partir du service.  Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<fenêtres\>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Indique des informations d'identification Windows.  La valeur par défaut correspond aux informations d'identification du thread actuel.  Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## Notes  
 Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise.  Cette section de configuration peut également servir à spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)