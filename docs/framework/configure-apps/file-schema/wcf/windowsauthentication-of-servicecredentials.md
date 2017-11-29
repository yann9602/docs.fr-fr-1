---
title: '&lt;windowsAuthentication&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbc4c3413213aa36468fde6e84671de0e0a31c2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;windowsAuthentication&gt; de &lt;serviceCredentials&gt;
Spécifie les paramètres d'une information d'identification de service Windows.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceCredentials >  
\<windowsAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`includeWindowsGroups`|Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité. La valeur par défaut est `true`.<br /><br /> L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe. Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|`allowAnonymousLogons`|Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés. La valeur par défaut est `false`.<br /><br /> Lorsque l'attribut `clientCredentialType` d'une liaison a la valeur `Windows`, le système n'autorise pas d'appelants anonymes. Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système. Vous pouvez substituer ce comportement en utilisant cet attribut.<br /><br /> N'utilisez ce paramètre qu'avec beaucoup de précaution.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`. Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`. Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
