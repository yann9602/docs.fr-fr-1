---
title: "&lt;proxy&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7178527f369c698b0ab53aa41cb28dd0126436b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltproxygt-element-network-settings"></a>&lt;proxy&gt; élément (paramètres réseau)
Définit un serveur proxy.  
  
 \<configuration>  
\<System.NET >  
\<defaultProxy >  
\<proxy >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`autoDetect`|Spécifie si le proxy est détecté automatiquement. La valeur par défaut est `unspecified`.|  
|`bypassonlocal`|Spécifie si le proxy est contourné pour les ressources locales. Les ressources locales incluent le serveur local (http://localhost, http://loopback ou http://127.0.0.1) et un URI sans point (http://webserver). La valeur par défaut est `unspecified`.|  
|`proxyaddress`|Spécifie l’URI de proxy à utiliser.|  
|`scriptLocation`|Spécifie l’emplacement du script de configuration.|  
|`usesystemdefault`|Spécifie s’il faut utiliser les paramètres de proxy Internet Explorer. Si la valeur `true`, les attributs suivants remplacent les paramètres de proxy Internet Explorer. La valeur par défaut est `unspecified`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configure le serveur proxy HTTP (Hypertext Transfer Protocol).|  
  
## <a name="text-value"></a>Valeur texte  
  
## <a name="remarks"></a>Remarques  
 Le `proxy` élément définit un serveur proxy pour une application. Si cet élément est manquant dans le fichier de configuration, le .NET Framework utilise les paramètres de proxy dans Internet Explorer.  
  
 La valeur de la `proxyaddress` attribut doit être un bien formé URI Uniform Resource Indicator ().  
  
 Le `scriptLocation` attribut fait référence à la détection automatique des scripts de configuration de proxy. Le <xref:System.Net.WebProxy> classe tente de localiser un script de configuration (généralement nommé Wpad.dat) lorsque le **utiliser le script de configuration automatique** option est sélectionnée dans Internet Explorer.  
  
 Utilisez le `usesystemdefault` attribut pour les applications .NET Framework version 1.1 qui effectuent une migration vers la version 2.0.  
  
 Une exception est levée si le `proxyaddress` attribut spécifie un proxy par défaut non valide. La propriété <xref:System.Exception.InnerException%2A> de l'exception fournit normalement plus d'informations sur la cause première de l'erreur.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise les valeurs par défaut du proxy Internet Explorer, spécifie l’adresse proxy et contourne le proxy pour l’accès local.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
