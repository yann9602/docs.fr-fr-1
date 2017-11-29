---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 48e5be23b196a24a9d3e2a1dc4639d8ca9823660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="f32d7-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="f32d7-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="f32d7-103">Inscrit un gestionnaire de l’authentification par revendications pour les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="f32d7-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="f32d7-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="f32d7-104">\<system.identityModel></span></span>  
<span data-ttu-id="f32d7-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f32d7-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f32d7-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="f32d7-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32d7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f32d7-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f32d7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f32d7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f32d7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f32d7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f32d7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f32d7-110">Attributes</span></span>  
  
|<span data-ttu-id="f32d7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f32d7-111">Attribute</span></span>|<span data-ttu-id="f32d7-112">Description</span><span class="sxs-lookup"><span data-stu-id="f32d7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f32d7-113">type</span><span class="sxs-lookup"><span data-stu-id="f32d7-113">type</span></span>|<span data-ttu-id="f32d7-114">Spécifie un type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="f32d7-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="f32d7-115">Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé].</span><span class="sxs-lookup"><span data-stu-id="f32d7-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f32d7-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f32d7-116">Child Elements</span></span>  
 <span data-ttu-id="f32d7-117">S’il existe aucune `type` attribut, ou si le `type` les références d’attribut le <xref:System.Security.Claims.ClaimsAuthenticationManager> (classe), le `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthenticationManager> peut définir des éléments de configuration enfants.</span><span class="sxs-lookup"><span data-stu-id="f32d7-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f32d7-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f32d7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f32d7-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f32d7-119">Element</span></span>|<span data-ttu-id="f32d7-120">Description</span><span class="sxs-lookup"><span data-stu-id="f32d7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f32d7-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f32d7-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="f32d7-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="f32d7-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f32d7-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="f32d7-123">Remarks</span></span>  
 <span data-ttu-id="f32d7-124">Le comportement par défaut fourni par le biais du <xref:System.Security.Claims.ClaimsAuthenticationManager> classe renvoie les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="f32d7-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="f32d7-125">Si aucun `type` attribut est spécifié ou si le `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthenticationManager> (classe), le `<claimsAuthenticationManager>` élément ne prend pas d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="f32d7-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="f32d7-126">Vous pouvez spécifier le `type` attribut pour enregistrer un type dérivé de la <xref:System.Security.Claims.ClaimsAuthenticationManager> classe pour implémenter un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f32d7-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="f32d7-127">Les classes dérivées peuvent prendre en charge la configuration par le biais des éléments enfants de la `<claimsAuthenticationManager>` élément en remplaçant le <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments.</span><span class="sxs-lookup"><span data-stu-id="f32d7-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="f32d7-128">Le schéma défini pour les éléments enfants est sur le Concepteur de la classe.</span><span class="sxs-lookup"><span data-stu-id="f32d7-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="f32d7-129">Le `<claimsAuthenticationManager>` élément définit les <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="f32d7-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f32d7-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="f32d7-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
