---
title: "&lt;Supprimez&gt; , élément pour webRequestModules (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 43f0d30f8c18c4755f31d0c851c773207bc15b78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a>&lt;Supprimez&gt; , élément pour webRequestModules (paramètres réseau)
Supprime un module de demande Web personnalisé de l’application.  
  
 \<configuration>  
\<System.NET >  
\<webRequestModules >  
\<Supprimer >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`prefix`|Le préfixe URI pour les demandes gérées par ce module de demande Web.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.|  
  
## <a name="remarks"></a>Remarques  
 Le `remove` élément supprime le module de demande Web inscrit pour le préfixe URI spécifié.  
  
 La valeur de la `prefix` attribut doit-elle être les premiers caractères d’un URI valide, par exemple, « http » ou « http://www.contoso.com ».  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime le module de demande Web existant pour HTTP et inscrit un nouveau module de demande Web personnalisé pour les demandes HTTP www.contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.WebRequest>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
