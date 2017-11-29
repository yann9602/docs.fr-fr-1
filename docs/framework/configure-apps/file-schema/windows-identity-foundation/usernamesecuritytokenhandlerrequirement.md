---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4ffe9764eb730be4859fb66ae2f0cc845c9404e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a>&lt;userNameSecurityTokenHandlerRequirement&gt;
Fournit la configuration pour la <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> classe ou les classes dérivées.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<userNameSecurityTokenHandlerRequirement >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|membershipProviderName|Spécifie le <xref:System.Web.Security.MembershipProvider> qui doit être utilisé par le Gestionnaire de jetons de sécurité.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Ajoute le Gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.|  
  
## <a name="remarks"></a>Remarques  
 Le `<userNameSecurityTokenHandlerRequirement>` ensembles d’éléments le <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> propriété lorsqu’un <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> objet est initialisé à partir de la configuration.  
  
## <a name="example"></a>Exemple  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
