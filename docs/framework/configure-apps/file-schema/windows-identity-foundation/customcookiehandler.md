---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: df95e8d47d6a19e4fd488fa14bc771bc2c2b56b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="1509c-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="1509c-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="1509c-103">Définit le type de gestionnaire de cookie personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1509c-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="1509c-104">Cet élément peut uniquement être présent si la `mode` attribut de la `<cookieHandler>` élément est « Custom ».</span><span class="sxs-lookup"><span data-stu-id="1509c-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="1509c-105">Le type personnalisé doit être dérivé du <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="1509c-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="1509c-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="1509c-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="1509c-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1509c-107">\<federationConfiguration></span></span>  
<span data-ttu-id="1509c-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="1509c-108">\<cookieHandler></span></span>  
<span data-ttu-id="1509c-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="1509c-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1509c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1509c-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1509c-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1509c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1509c-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1509c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1509c-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="1509c-113">Attributes</span></span>  
  
|<span data-ttu-id="1509c-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="1509c-114">Attribute</span></span>|<span data-ttu-id="1509c-115">Description</span><span class="sxs-lookup"><span data-stu-id="1509c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1509c-116">type</span><span class="sxs-lookup"><span data-stu-id="1509c-116">type</span></span>|<span data-ttu-id="1509c-117">Spécifie un type personnalisé qui dérive de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="1509c-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="1509c-118">Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1509c-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1509c-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1509c-119">Child Elements</span></span>  
 <span data-ttu-id="1509c-120">None</span><span class="sxs-lookup"><span data-stu-id="1509c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1509c-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1509c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1509c-122">Élément</span><span class="sxs-lookup"><span data-stu-id="1509c-122">Element</span></span>|<span data-ttu-id="1509c-123">Description</span><span class="sxs-lookup"><span data-stu-id="1509c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1509c-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="1509c-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="1509c-125">Configure le <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="1509c-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1509c-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="1509c-126">Remarks</span></span>  
 <span data-ttu-id="1509c-127">Lorsque vous spécifiez un gestionnaire de cookie personnalisé en définissant le `mode` attribut de la `<cookieHandler>` élément à « Custom », vous devez spécifier le type du Gestionnaire de cookie personnalisé en incluant un `<customCookieHandler>` élément enfant qui fait référence au type de gestionnaire de cookie.</span><span class="sxs-lookup"><span data-stu-id="1509c-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="1509c-128">Cet élément ne peut pas être spécifié quand le `mode` attribut a la valeur « Chunked » ou « Default ».</span><span class="sxs-lookup"><span data-stu-id="1509c-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="1509c-129">Gestionnaires de cookie personnalisé doivent dériver de la <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="1509c-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="1509c-130">Le `<customCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="1509c-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1509c-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="1509c-131">Example</span></span>  
 <span data-ttu-id="1509c-132">L’exemple suivant configure le SAM pour utiliser un gestionnaire de cookie personnalisé de type `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="1509c-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1509c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1509c-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
