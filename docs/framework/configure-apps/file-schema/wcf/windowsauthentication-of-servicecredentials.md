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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8af7d89fdf09316594bc8ef3433e2b47e8fb0a7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="e5416-102">&lt;windowsAuthentication&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="e5416-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="e5416-103">Spécifie les paramètres d'une information d'identification de service Windows.</span><span class="sxs-lookup"><span data-stu-id="e5416-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="e5416-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e5416-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5416-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e5416-105">\<behaviors></span></span>  
<span data-ttu-id="e5416-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e5416-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e5416-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="e5416-107">\<behavior></span></span>  
<span data-ttu-id="e5416-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e5416-108">\<serviceCredentials></span></span>  
<span data-ttu-id="e5416-109">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e5416-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5416-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5416-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5416-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5416-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5416-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e5416-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5416-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e5416-113">Attributes</span></span>  
  
|<span data-ttu-id="e5416-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5416-114">Attribute</span></span>|<span data-ttu-id="e5416-115">Description</span><span class="sxs-lookup"><span data-stu-id="e5416-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="e5416-116">Attribut à valeur booléenne facultatif qui spécifie si le système inclut des groupes Windows dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e5416-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="e5416-117">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="e5416-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="e5416-118">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait qu'elle provoque une expansion complète du groupe.</span><span class="sxs-lookup"><span data-stu-id="e5416-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="e5416-119">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e5416-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="e5416-120">Attribut à valeur booléenne facultatif qui spécifie si les appelants anonymes et non authentifiés sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e5416-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="e5416-121">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="e5416-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e5416-122">Lorsque l'attribut `clientCredentialType` d'une liaison a la valeur `Windows`, le système n'autorise pas d'appelants anonymes.</span><span class="sxs-lookup"><span data-stu-id="e5416-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="e5416-123">Cela signifie que seuls les appelants authentifiés du domaine ou du groupe de travail sont autorisés à accéder au système.</span><span class="sxs-lookup"><span data-stu-id="e5416-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="e5416-124">Vous pouvez substituer ce comportement en utilisant cet attribut.</span><span class="sxs-lookup"><span data-stu-id="e5416-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="e5416-125">N'utilisez ce paramètre qu'avec beaucoup de précaution.</span><span class="sxs-lookup"><span data-stu-id="e5416-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5416-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5416-126">Child Elements</span></span>  
 <span data-ttu-id="e5416-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e5416-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5416-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5416-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e5416-129">Élément</span><span class="sxs-lookup"><span data-stu-id="e5416-129">Element</span></span>|<span data-ttu-id="e5416-130">Description</span><span class="sxs-lookup"><span data-stu-id="e5416-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5416-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e5416-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="e5416-132">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="e5416-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5416-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5416-133">Remarks</span></span>  
 <span data-ttu-id="e5416-134">Utilisez cet élément pour autoriser l'accès d'utilisateurs Windows anonymes en définissant l'attribut `allowAnonymousLogons`.</span><span class="sxs-lookup"><span data-stu-id="e5416-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="e5416-135">Vous pouvez également indiquer s'il faut inclure des informations sur les groupes auxquels les utilisateurs appartiennent dans AuthorizationContext en définissant l'attribut `includeWindowsGroups`.</span><span class="sxs-lookup"><span data-stu-id="e5416-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="e5416-136">Si ce dernier a la valeur `true` (paramètre par défaut), le service peut déterminer les groupes Windows auxquels le client appartient.</span><span class="sxs-lookup"><span data-stu-id="e5416-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5416-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5416-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
