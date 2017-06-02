---
title: "&lt;transport&gt; de &lt;wsHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;transport&gt; de &lt;wsHttpBinding&gt;
Définit les paramètres d'authentification correspondant au transport HTTP.  
  
## Syntaxe  
  
```  
  
<wsHttpBinding>  
    <binding>  
        <security mode=”None|Transport|TransportWithMessageCredential|TransportCredentialOnly”>  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement=”Never|WhenSupported|Always” protectionScenario=”TransportSelected|TrustedProxy”>  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## Type  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`clientCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès du service.  Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Spécifie les informations d'identification utilisées pour authentifier le client auprès d'un proxy de domaine.  Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Chaîne indiquant le domaine de l'authentification de base ou Digest.  La valeur par défaut est une chaîne vide.<br /><br /> Un domaine d'authentification spécifie au moins le nom de l'hôte qui exécute l'authentification.  Il peut également spécifier une collection d'utilisateurs disposant d'un accès.  Un utilisateur peut interroger le domaine d'authentification pour vérifier quels noms d'utilisateurs et mots de passe peuvent être utilisés.|  
|`policyEnforcement`|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1.  Never : la stratégie n'est jamais appliquée \(la protection étendue est désactivée\).<br />2.  WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3.  Always : la stratégie est toujours appliquée.  Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|  
  
## Attribut clientCredentialType  
  
|Valeur|Description|  
|------------|-----------------|  
|`None`|La sécurité est désactivée.|  
|`Basic`|Utilise l'authentification de base.|  
|`Digest`|Utilise l'authentification Digest.|  
|`Ntlm`|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|  
|`Windows`|Utilise l'authentification intégrée Windows.|  
|`Certificate`|Utilise des certificats X.509 pour authentifier le client.|  
  
## Attribut proxyCredentialType  
  
|Valeur|Description|  
|------------|-----------------|  
|`None`|La sécurité est désactivée.|  
|`Basic`|Utilise l'authentification de base.|  
|`Digest`|Utilise l'authentification Digest.|  
|`Ntlm`|Utilise l'authentification NTLM comme solution de secours dans un domaine Windows.|  
|`Windows`|Utilise l'authentification intégrée Windows.|  
|`Certificate`|Utilise des certificats X.509 pour authentifier le client.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Représente les fonctionnalités de sécurité de [\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## Voir aussi  
 <xref:System.ServiceModel.HttpTransportSecurity>   
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)