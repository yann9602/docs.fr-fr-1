---
title: '&lt;serviceTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 06e871ee31880a219d9105ff4ce667618bfb78f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Inscrit le résolveur de jeton de service qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons. Le programme de résolution de jeton de service permet de résoudre le jeton de chiffrement sur les jetons et les messages entrant.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Spécifie le type du programme de résolution de jeton de service. Soit le <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe. Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé]. Obligatoire.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit des gestionnaires de jetons de configuration pour une collection de sécurité.|  
  
## <a name="remarks"></a>Remarques  
 Le programme de résolution de jeton de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrant. Il est utilisé pour récupérer la clé doit être utilisée pour déchiffrer les jetons entrants. Vous devez spécifier le `type` attribut. Le type spécifié peut être <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.  
  
 Certains gestionnaires de jetons permettent de spécifier les paramètres de résolution de jeton de service dans la configuration. Paramètres de gestionnaires de jetons individuels remplacent celles spécifiées dans la collection de gestionnaire de jetons de sécurité.  
  
> [!NOTE]
>  En spécifiant le `<serviceTokenResolver>` élément comme un élément enfant de le [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) l’élément a été déconseillée, mais est toujours prise en charge pour la compatibilité descendante. Paramètres de la `<securityTokenHandlerConfiguration>` élément remplacent celles sur le `<identityConfiguration>` élément.  
  
## <a name="example"></a>Exemple  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
