---
title: "&lt;defaultHttpCachePolicy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultHttpCachePolicy> (élément)"
  - "defaultHttpCachePolicy (élément)"
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;defaultHttpCachePolicy&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.  
  
## Syntaxe  
  
```  
< defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss"|"minValue"  
  maximumAge  ="d.hh:mm:ss"|"maxValue"  
  maximumStale="d.hh:mm:ss"|"maxValue"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`maximumAge`|Spécifie l'intervalle de temps maximal avant qu'un objet mis en cache soit marqué comme expiré.|  
|`maximumStale`|Spécifie le délai maximal devant s'écouler après l'heure de nouveauté calculée, avant qu'un objet mis en cache soit marqué comme expiré.|  
|`minimumFresh`|Spécifie le délai minimum pour qu'un objet mis en cache soit considéré comme nouveau.|  
|`policyLevel`|Spécifie si la stratégie de mise en cache est automatique, ou si le cache est ignoré.  La valeur par défaut est `BypassCache`.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
  
## Notes  
 La valeur de l'attribut `policyLevel` est `BypassCache` ou `Default`.  
  
 Les valeurs pour les éléments `maximumAge`, `maximumStale` et `minimumFresh` correspondent soit à un intervalle de temps explicite au format *d.* *:hh*:*mm* *ss* \(jours, heures, minutes et secondes\) soit aux constantes ou `minValue` ou `maxValue` selon le cas.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant indique comment spécifier un délai de nouveauté minimum de six heures, un âge maximal de deux jours, et un délai de péremption maximal de quatre heures.  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy>  
        <set minimumFresh="0.06:00:00" />  
        <set maximumAge  ="2.00:00:00" />  
        <set maximumStale="0.04:00:00" />  
      </defaultHttpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)