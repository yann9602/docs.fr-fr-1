---
title: "&lt;userNameAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;userNameAuthentication&gt;
Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.  
  
## Syntaxe  
  
```  
  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`cacheLogonTokenLifetime`|<xref:System.Timespan> qui spécifie la durée maximale de mise en cache d'un jeton.  La valeur par défaut est 00:15:00.|  
|`cacheLogonTokens`|Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache.  La valeur par défaut est `false`.|  
|`customUserNamePasswordValidatorType`|Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser.  La valeur par défaut est une chaîne vide.|  
|`includeWindowsGroups`|Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité.  La valeur par défaut est `true`.<br /><br /> L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.  Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.|  
|`maxCacheLogonTokens`|Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache.  Cette valeur doit être supérieure à zéro.  La valeur par défaut est 128.|  
|`membershipProviderName`|Lorsque l'attribut `clientCredentialType` d'une liaison a la valeur `username`, le nom d'utilisateur est mappé aux comptes Windows.  Vous pouvez substituer ce comportement à l'aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.|  
|`userNamePasswordValidationMode`|Spécifie la manière dont le mot de passe de nom d'utilisateur est validé.  Les valeurs valides sont les suivantes :<br /><br /> -   Windows<br />-   MembershipProvider<br />-   Personnalisé<br /><br /> Le paramètre par défaut est Windows.  Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l'information d'identification du client.|  
  
## Notes  
 Si aucune des liaisons utilisées par un service n'est configurée pour l'authentification par nom d'utilisateur\/mot de passe, les attributs de cet élément sont ignorés.  Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.  
  
 Si aucun des liaisons utilisées par un service n'est configurée pour utiliser l'authentification Windows par nom d'utilisateur\/mot de passe, les paramètres en rapport avec la mise en cache des jetons d'ouverture de session sont ignorés.  Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>