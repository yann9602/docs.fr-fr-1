---
title: '&lt;cookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 88e968d025c959ec33674a9d8edb5e63341433ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Configure le <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) utilise pour lire et écrire des cookies.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Spécifie le nom de base pour tout cookie écrit. La valeur par défaut est « FedAuth ».|  
|path|Spécifie la valeur de chemin d’accès pour tout cookie écrit. La valeur par défaut est « Place du HttpRuntime.AppDomainAppVirtualPath ».|  
|mode|Parmi les <xref:System.IdentityModel.Services.CookieHandlerMode> valeurs qui spécifie le type de gestionnaire de cookie utilisé par le SAM. Les valeurs suivantes peuvent être utilisées :<br /><br /> -« Default », le même que « Chunked ».<br />-« Mémorisé en bloc », utilise une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Ce gestionnaire de cookie garantit que des cookies ne dépassent pas une taille maximale du jeu. Pour ce faire, il potentiellement « segmentation » un cookie logique en plusieurs cookies sur simultanée.<br />-« Custom », utilise une instance d’une classe personnalisée dérivée de <xref:System.IdentityModel.Services.CookieHandler>. La classe dérivée est référencée par le `<customCookieHandler>` élément enfant.<br /><br /> La valeur par défaut est « Default ».|  
|persistentSessionLifetime|Spécifie la durée de vie de sessions persistantes. Si zéro, les sessions temporaires sont toujours utilisées. La valeur par défaut est « 0:0:0 », qui spécifie une session temporaire. La valeur maximale est « 365:0:0 », qui spécifie une session de 365 jours. La valeur doit être spécifiée en fonction de la restriction suivante : `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, où la valeur la plus à gauche indique les jours, la valeur médiane (le cas échéant) spécifie les heures et la valeur plus à droite (le cas échéant) spécifie les minutes.|  
|RequireSsl|Spécifie si l’indicateur « Sécurisé » est émis pour tout cookie écrit. Si cette valeur est définie, les cookies de session seront uniquement accessible via le protocole HTTPS. La valeur par défaut est "true".|  
|hideFromScript|Contrôle si l’indicateur « HttpOnly » est émis pour tout cookie écrit. Certains navigateurs web respectent cet indicateur en conservant un script côté client d’accéder à la valeur du cookie. La valeur par défaut est "true".|  
|de domaine|La valeur de domaine pour tout cookie écrit. La valeur par défaut est "".|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Cet élément peut uniquement être présent si la `mode` attribut de la `<cookieHandler>` élément est « Default » ou « Mémorisé en bloc ».|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Définit le type de gestionnaire de cookie personnalisé. Cet élément doit être présent si la `mode` attribut de la `<cookieHandler>` élément est « Custom ». Il ne peut pas être présent pour toutes les autres valeurs de la `mode` attribut. Le type personnalisé doit être dérivé du <xref:System.IdentityModel.Services.CookieHandler> classe.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Remarques  
 Le <xref:System.IdentityModel.Services.CookieHandler> est responsable de lire et écrire des cookies brutes sur le protocole HTTP au niveau du protocole. Vous pouvez configurer un <xref:System.IdentityModel.Services.ChunkedCookieHandler> ou un gestionnaire de cookie personnalisé dérivé de la <xref:System.IdentityModel.Services.CookieHandler> classe.  
  
 Pour configurer un gestionnaire de cookie mémorisé en bloc, définissez l’attribut mode « Chunked » ou « Default ». La taille de segment par défaut est 2 000 octets, mais vous pouvez choisir une taille de segment différent en incluant un `<chunkedCookieHandler>` élément enfant.  
  
 Pour configurer un gestionnaire personnalisé de cookie, définissez l’attribut mode à « Custom ». Vous devez également spécifier un `<customCookieHandler>` élément enfant qui fait référence au type de votre gestionnaire personnalisé.  
  
 Le `<cookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.CookieHandlerElement> classe. Le Gestionnaire de cookie qui a été spécifié dans la configuration est disponible à partir de la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> propriété de la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet définie sur le <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre un `<cookieHandler>` élément. Dans cet exemple, étant donné que le `mode` attribut n’est pas spécifié, le Gestionnaire de cookie par défaut sera utilisé par le SAM. Il s’agit d’une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe. Étant donné que le `<chunkedCookieHandler>` élément enfant n’est pas spécifié, la taille de segment par défaut sera utilisée. HTTPS n’est plus nécessaire car le `requireSsl` attribut a la valeur `false`.  
  
> [!WARNING]
>  Dans cet exemple, HTTPS n’est pas requis pour écrire les cookies de session. C’est parce que le `requireSsl` de l’attribut le `<cookieHandler>` a la valeur `false`. Ce paramètre n’est pas recommandé pour la plupart des environnements de production, car elle peut présenter un risque de sécurité.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
