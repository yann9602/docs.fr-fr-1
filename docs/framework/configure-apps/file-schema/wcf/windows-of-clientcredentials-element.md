---
title: "&lt;windows&gt;, élément de &lt;clientCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cf2740b0218286178e62262723bb060dc2d3817
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a>&lt;windows&gt;, élément de &lt;clientCredentials&gt;
Spécifie les paramètres pour des informations d'identification Windows à utiliser pour représenter le client.  
  
 \<système. ServiceModel >  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
\<clientCredentials >  
\<Windows >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Définit la préférence d'emprunt d'identité que le client communique au serveur. Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur. Les valeurs valides sont les suivantes :<br /><br /> -Identification : Le serveur peut obtenir l’identité et les privilèges du client, mais ne peut pas l’identité du client.<br />-L’emprunt d’identité : Le serveur peut emprunter l’identité de contexte de sécurité du client sur le système local.<br />-Delegation : Le serveur peut emprunter l’identité de contexte de sécurité du client sur les systèmes distants.<br />-Anonyme : Le serveur ne peut pas emprunter l’identité ou identifier le client.<br />-None : Un niveau d’emprunt d’identité n’est affecté.<br /><br /> La valeur par défaut est Identification. Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|L'affectation de la valeur `true` à cette propriété permet de rétrograder l'authentification à NTLM si Kerberos n'est pas disponible.<br /><br /> Si la valeur `false` est affectée à cette propriété, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tente de lever, d'après le mode Best effort, une exception si NTLM est utilisé. Notez que l'affectation de la valeur `false` à cette propriété peut ne pas empêcher la transmission des informations d'identification NTLM.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [Sécurisation des clients](../../../../../docs/framework/wcf/securing-clients.md)  
 [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Sécurisation des Services et Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
