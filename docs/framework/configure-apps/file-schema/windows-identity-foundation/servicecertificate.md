---
title: "&lt;serviceCertificate&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;serviceCertificate&gt;
Configure le certificat X.509 utilisé pour crypter et décrypter les jetons.  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<certificateReference\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|Spécifie les paramètres qui sont utilisés pour trouver et valider un certificat X.509 dans un magasin de certificats.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\).|  
  
## Exemple  
 Le code XML suivant illustre l'utilisation de la \<serviceCertificate\> élément.  Le code XML provient de la `CustomToken` exemple.  
  
```  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```