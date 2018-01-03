---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f388369d4dc2e590473ad98189ade70b77551b10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
Inscrit un cache de relecture de jetons avec un service ou d’une collection de gestionnaire de jetons de sécurité.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<met en cache >  
\<tokenReplayCache >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Un type qui dérive de la <xref:System.IdentityModel.Tokens.TokenReplayCache> classe. Pour plus d’informations sur la façon de spécifier une personnalisée `type`, voir [références de Type personnalisé].
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<met en cache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Inscrit le met en cache utilisé par un service ou une collection de gestionnaire de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  
 Le cache de relecture de jetons est utilisé pour détecter les jetons relus. Détection de relecture de jetons est activée par le [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) élément, qui spécifie également l’heure d’expiration maximal pour les jetons.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant illustre la configuration d’un cache personnalisé pour la détection des jetons relus.  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
