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
ms.openlocfilehash: fded506ce695473843c29a7438fe4818cab8bd91
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="72ce4-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="72ce4-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="72ce4-103">Spécifie les informations d'identification d'un service selon le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="72ce4-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="72ce4-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="72ce4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72ce4-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="72ce4-105">\<behaviors></span></span>  
<span data-ttu-id="72ce4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="72ce4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="72ce4-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="72ce4-107">\<behavior></span></span>  
<span data-ttu-id="72ce4-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="72ce4-108">\<serviceCredentials></span></span>  
<span data-ttu-id="72ce4-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="72ce4-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ce4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72ce4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72ce4-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="72ce4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72ce4-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="72ce4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72ce4-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="72ce4-113">Attributes</span></span>  
  
|<span data-ttu-id="72ce4-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="72ce4-114">Attribute</span></span>|<span data-ttu-id="72ce4-115">Description</span><span class="sxs-lookup"><span data-stu-id="72ce4-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="72ce4-116"><xref:System.TimeSpan> qui spécifie la durée maximale de mise en cache d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="72ce4-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="72ce4-117">La valeur par défaut est 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="72ce4-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="72ce4-118">Valeur booléenne qui spécifie si les jetons d'ouverture de session sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="72ce4-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="72ce4-119">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="72ce4-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="72ce4-120">Chaîne qui spécifie le type de validateur de mot de passe de nom d'utilisateur personnalisé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="72ce4-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="72ce4-121">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="72ce4-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="72ce4-122">Valeur booléenne qui spécifie si les groupes Windows sont inclus au contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="72ce4-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="72ce4-123">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="72ce4-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="72ce4-124">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="72ce4-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="72ce4-125">Affectez la valeur `false` à cette propriété s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="72ce4-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="72ce4-126">Entier qui spécifie le nombre maximal de jetons d'ouverture de session à mettre en cache.</span><span class="sxs-lookup"><span data-stu-id="72ce4-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="72ce4-127">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="72ce4-127">This value should be larger than zero.</span></span> <span data-ttu-id="72ce4-128">La valeur par défaut est 128.</span><span class="sxs-lookup"><span data-stu-id="72ce4-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="72ce4-129">Lorsque l'attribut `clientCredentialType` d'une liaison a la valeur `username`, le nom d'utilisateur est mappé aux comptes Windows.</span><span class="sxs-lookup"><span data-stu-id="72ce4-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="72ce4-130">Vous pouvez substituer ce comportement à l'aide de cet attribut, qui est une chaîne contenant le nom de la valeur <xref:System.Web.Security.MembershipProvider> qui fournit le mécanisme de validation du mot de passe pertinent.</span><span class="sxs-lookup"><span data-stu-id="72ce4-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="72ce4-131">Spécifie la manière dont le mot de passe de nom d'utilisateur est validé.</span><span class="sxs-lookup"><span data-stu-id="72ce4-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="72ce4-132">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="72ce4-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="72ce4-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="72ce4-133">-   Windows</span></span><br /><span data-ttu-id="72ce4-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="72ce4-134">-   MembershipProvider</span></span><br /><span data-ttu-id="72ce4-135">-Custom</span><span class="sxs-lookup"><span data-stu-id="72ce4-135">-   Custom</span></span><br /><br /> <span data-ttu-id="72ce4-136">Le paramètre par défaut est Windows.</span><span class="sxs-lookup"><span data-stu-id="72ce4-136">The default is Windows.</span></span> <span data-ttu-id="72ce4-137">Cet attribut est de type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="72ce4-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72ce4-138">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="72ce4-138">Child Elements</span></span>  
 <span data-ttu-id="72ce4-139">Aucun.</span><span class="sxs-lookup"><span data-stu-id="72ce4-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72ce4-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="72ce4-140">Parent Elements</span></span>  
  
|<span data-ttu-id="72ce4-141">Élément</span><span class="sxs-lookup"><span data-stu-id="72ce4-141">Element</span></span>|<span data-ttu-id="72ce4-142">Description</span><span class="sxs-lookup"><span data-stu-id="72ce4-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72ce4-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="72ce4-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="72ce4-144">Spécifie l’information d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation de l’information d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="72ce4-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ce4-145">Remarques</span><span class="sxs-lookup"><span data-stu-id="72ce4-145">Remarks</span></span>  
 <span data-ttu-id="72ce4-146">Si aucune des liaisons utilisées par un service n’est configurée pour l’authentification par nom d’utilisateur/mot de passe, les attributs de cet élément sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="72ce4-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="72ce4-147">Il s'agit notamment de `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` et `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="72ce4-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="72ce4-148">Si aucun des liaisons utilisées par un service n'est configurée pour utiliser l'authentification Windows par nom d'utilisateur/mot de passe, les paramètres en rapport avec la mise en cache des jetons d'ouverture de session sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="72ce4-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="72ce4-149">Il s'agit notamment de `cacheLogonTokenLifetime`, `cacheLogonTokens` et `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="72ce4-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ce4-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72ce4-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
