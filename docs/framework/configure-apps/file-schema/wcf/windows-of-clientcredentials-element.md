---
title: "&lt;windows&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;windows&gt;, &#233;l&#233;ment de &lt;clientCredentials&gt;
Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.  
  
## Syntaxe  
  
```  
  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`allowedImpersonationLevel`|Définit la préférence d'emprunt d'identité que le client communique au serveur.  Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.  Les valeurs valides sont les suivantes :<br /><br /> -   Identification : le serveur peut obtenir l'identité et les privilèges du client, mais ne peut pas emprunter l'identité du client.<br />-   Impersonation : le serveur peut emprunter l'identité du contexte de sécurité du client sur le système local.<br />-   Delegation : le serveur peut emprunter l'identité du contexte de sécurité du client sur les systèmes distants.<br />-   Anonymous : le serveur ne peut pas emprunter l'identité du client ni l'identifier.<br />-   None : aucun niveau d'emprunt d'identité n'est assigné.<br /><br /> La valeur par défaut est Identification.  Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.<br /><br /> Si la valeur `false` est affectée à cette propriété, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tente de lever, d'après le mode Best effort, une exception si NTLM est utilisé.  Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>   
 <xref:System.ServiceModel.Security.WindowsClientCredential>   
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)   
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)