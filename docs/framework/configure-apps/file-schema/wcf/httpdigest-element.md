---
title: "&lt;httpDigest&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;httpDigest&gt;, &#233;l&#233;ment
Spécifie une information d'identification de type condensé utilisée lors de l'authentification du client à un service.  
  
## Syntaxe  
  
```  
  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`impersonationLevel`|Définit la préférence d'emprunt d'identité que le client communique au serveur.  Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.  Les valeurs valides sont les suivantes :<br /><br /> -   Identification : le serveur peut obtenir l'identité et les privilèges du client, mais ne peut pas emprunter l'identité du client.<br />-   Impersonation : le serveur peut emprunter l'identité du contexte de sécurité du client sur le système local.<br />-   Delegation : le serveur peut emprunter l'identité du contexte de sécurité du client sur les systèmes distants.<br />-   Anonymous : le serveur ne peut pas emprunter l'identité du client ni l'identifier.<br />-   None : aucun niveau d'emprunt d'identité n'est assigné.<br /><br /> La valeur par défaut est Identification.  Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.|  
  
## Notes  
 Un Digest est un hachage déterminé à l'aide d'un algorithme et d'un jeu d'entrées.  L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées.  Le client peut calculer le hachage et l'envoyer au service.  Le service calcule également le hachage et compare les valeurs.  Une correspondance valide le client.  
  
 Cette fonction doit être activée avec Active Directory sur Windows et les services IIS \(Internet Information Services\).  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Authentification Digest dans IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>   
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>   
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)