---
title: '&lt;userNameAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea18a2c8c2244f384b87b48f195b77da4eb5dfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusernameauthenticationgt"></a>&lt;userNameAuthentication&gt;
Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceCredentials >  
\<userNameAuthentication >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<xref:System.TimeSpan> qui spécifie la durée maximale de mise en cache d'un jeton. La valeur par défaut est 00:15:00.|  
|`cacheLogonTokens`|Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache. La valeur par défaut est `false`.|  
|`customUserNamePasswordValidatorType`|Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser. La valeur par défaut est une chaîne vide.|  
|`includeWindowsGroups`|Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité. La valeur par défaut est `true`.<br /><br /> L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe. Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|`maxCacheLogonTokens`|Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache. Cette valeur doit être supérieure à zéro. La valeur par défaut est 128.|  
|`membershipProviderName`|Lorsque l'attribut `clientCredentialType` d'une liaison a la valeur `username`, le nom d'utilisateur est mappé aux comptes Windows. Vous pouvez substituer ce comportement à l'aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.|  
|`userNamePasswordValidationMode`|Spécifie la manière dont le mot de passe de nom d'utilisateur est validé. Les valeurs valides sont les suivantes :<br /><br /> -Windows<br />-MembershipProvider<br />-Custom<br /><br /> Le paramètre par défaut est Windows. Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.|  
  
## <a name="remarks"></a>Notes  
 Si aucune des liaisons utilisées par un service n’est configurée pour l’authentification par nom d’utilisateur/mot de passe, les attributs de cet élément sont ignorés. Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.  
  
 Si aucun des liaisons utilisées par un service n'est configurée pour utiliser l'authentification Windows par nom d'utilisateur/mot de passe, les paramètres en rapport avec la mise en cache des jetons d'ouverture de session sont ignorés. Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
