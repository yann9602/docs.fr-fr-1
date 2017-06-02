---
title: "&lt;cookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;cookieHandler&gt;
Configure la <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) utilise pour lire et écrire des cookies.  
  
## Syntaxe  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Spécifie le nom de base pour tous les cookies écrits.  La valeur par défaut est « FedAuth ».|  
|path|Spécifie la valeur de chemin d'accès pour tous les cookies écrits.  La valeur par défaut est « HttpRuntime.AppDomainAppVirtualPath ».|  
|mode|Parmi les <xref:System.IdentityModel.Services.CookieHandlerMode> valeurs qui spécifie le type de Gestionnaire de cookie utilisé par le SAM.  Les valeurs suivantes peuvent être utilisées :<br /><br /> -   « Default »: identique à « Chunked ».<br />-   « Segmenté » — utilise une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe.  Ce gestionnaire de cookie garantit que les cookies individuels ne dépassent pas une taille maximale du jeu.  Pour ce faire, il potentiellement « segmentation » un seul cookie logique dans un certain nombre de cookies on\-the\-wire.<br />-   « Personnalisé » — utilise une instance d'une classe personnalisée dérivée de <xref:System.IdentityModel.Services.CookieHandler>.  La classe dérivée est référencée par le `<customCookieHandler>` élément enfant.<br /><br /> La valeur par défaut est « Default ».|  
|persistentSessionLifetime|Spécifie la durée de vie des sessions persistantes.  Si zéro, sessions transitoires sont toujours utilisées.  La valeur par défaut est "0:0:0", qui spécifie une session en régime transitoire.  La valeur maximale est "365:0:0", qui spécifie une session de 365 jours.  La valeur doit être spécifiée en fonction de la restriction suivante : `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, où la valeur la plus à gauche indique les jours, la valeur médiane \(si présent\) spécifie les heures et la valeur à l'extrême droite \(si présent\) spécifie les minutes.|  
|requireSsl|Spécifie si l'indicateur « Sécurisé » est émis pour tous les cookies écrits.  Si cette valeur est définie, les cookies de session sign\-in sera uniquement disponibles via HTTPS.  La valeur par défaut est « true ».|  
|hideFromScript|Contrôle si l'indicateur « HttpOnly » est émis pour tous les cookies écrits.  Certains navigateurs web Honorer cet indicateur en conservant le script côté client d'accéder à la valeur du cookie.  La valeur par défaut est « true ».|  
|domaine|La valeur de domaine pour tous les cookies écrits.  La valeur par défaut est "".|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<chunkedCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Configure la <xref:System.IdentityModel.Services.ChunkedCookieHandler>.  Cet élément ne peut être présent si la `mode` l'attribut de la `<cookieHandler>` élément est « Default » ou « Chunked ».|  
|[\<customCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Définit le type de Gestionnaire de cookie personnalisé.  Cet élément doit être présent si la `mode` l'attribut de la `<cookieHandler>` élément est « Custom ».  Il ne peut pas être présent pour toutes les autres valeurs de la `mode` attribut.  Le type personnalisé doit être dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\).|  
  
## Notes  
 Le <xref:System.IdentityModel.Services.CookieHandler> est responsable de lire et écrire des cookies brutes à HTTP au niveau du protocole.  Vous pouvez configurer soit un <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou un gestionnaire de cookie personnalisé dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Pour configurer un gestionnaire de cookie mémorisé en bloc, définissez l'attribut mode « Chunked » ou « Default ».  La taille de segment par défaut est 2000 octets, mais vous pouvez éventuellement spécifier une taille de segment différent en incluant une `<chunkedCookieHandler>` élément enfant.  
  
 Pour configurer un gestionnaire de cookie personnalisé, définissez l'attribut mode sur « Custom ».  Vous devez également spécifier une `<customCookieHandler>` élément enfant qui fait référence au type de votre gestionnaire personnalisé.  
  
 Le `<cookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.CookieHandlerElement> classe.  Le Gestionnaire de cookie qui a été spécifié dans la configuration est disponible à partir de la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> propriété de la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet définie sur le <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName> propriété.  
  
## Exemple  
 Le XML suivant un `<cookieHandler>` élément.  Dans cet exemple, parce que le `mode` attribut n'est pas spécifié, le Gestionnaire de cookie par défaut sera utilisé par le SAM.  Il s'agit d'une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe.  Étant donné que la `<chunkedCookieHandler>` élément enfant n'est pas spécifié, la taille de segment par défaut sera utilisée.  HTTPS ne sera pas nécessaire car le `requireSsl` attribut a la valeur `false`.  
  
> [!WARNING]
>  Dans cet exemple, HTTPS n'est pas nécessaire d'écrire des cookies de session.  C'est parce que le `requireSsl` d'attribut sur le `<cookieHandler>` élément est définie sur `false`.  Ce paramètre n'est pas recommandé pour la plupart des environnements de production tel qu'il peut présenter un risque de sécurité.  
  
```  
<cookieHandler requireSsl="false" />  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.CookieHandler>   
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>