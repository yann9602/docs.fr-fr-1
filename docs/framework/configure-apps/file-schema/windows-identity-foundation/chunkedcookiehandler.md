---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 906a9e7cafca14dc4ee13dcb9eb9e59736464fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="8b8d1-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="8b8d1-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="8b8d1-103">Configure le <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="8b8d1-104">Cet élément peut uniquement être présent si la `mode` attribut de la `<cookieHandler>` élément est « Default » ou « Mémorisé en bloc ».</span><span class="sxs-lookup"><span data-stu-id="8b8d1-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="8b8d1-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="8b8d1-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="8b8d1-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8b8d1-106">\<federationConfiguration></span></span>  
<span data-ttu-id="8b8d1-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8b8d1-107">\<cookieHandler></span></span>  
<span data-ttu-id="8b8d1-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8b8d1-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8d1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b8d1-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b8d1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8b8d1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8b8d1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b8d1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b8d1-112">Attributes</span></span>  
  
|<span data-ttu-id="8b8d1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="8b8d1-113">Attribute</span></span>|<span data-ttu-id="8b8d1-114">Description</span><span class="sxs-lookup"><span data-stu-id="8b8d1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b8d1-115">taille du segment</span><span class="sxs-lookup"><span data-stu-id="8b8d1-115">chunkSize</span></span>|<span data-ttu-id="8b8d1-116">La taille maximale, en caractères, les données de cookie HTTP pour un cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="8b8d1-117">Vous devez être prudent lors de l’ajustement de la taille du segment.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="8b8d1-118">Navigateurs Web ont des limites différentes sur la taille des cookies et le nombre autorisé par domaine.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="8b8d1-119">Par exemple, la spécification Netscape d’origine prévu ces limites : total de 300 cookies, 4096 octets par en-tête cookie (y compris les métadonnées, pas seulement la valeur du cookie) et 20 cookies par domaine.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="8b8d1-120">La valeur par défaut est 2000.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-120">The default is 2000.</span></span> <span data-ttu-id="8b8d1-121">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b8d1-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b8d1-122">Child Elements</span></span>  
 <span data-ttu-id="8b8d1-123">None</span><span class="sxs-lookup"><span data-stu-id="8b8d1-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b8d1-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b8d1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8b8d1-125">Élément</span><span class="sxs-lookup"><span data-stu-id="8b8d1-125">Element</span></span>|<span data-ttu-id="8b8d1-126">Description</span><span class="sxs-lookup"><span data-stu-id="8b8d1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b8d1-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8b8d1-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="8b8d1-128">Configure le <xref:System.IdentityModel.Services.CookieHandler> qui le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) utilise pour lire et écrire des cookies.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b8d1-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="8b8d1-129">Remarks</span></span>  
 <span data-ttu-id="8b8d1-130">Lorsque vous spécifiez un <xref:System.IdentityModel.Services.ChunkedCookieHandler> en définissant le `mode` attribut de la `<cookieHandler>` élément « Default » ou « Chunked », vous pouvez spécifier la taille de segment par le Gestionnaire de cookie pour lire et écrire des cookies en incluant un `<chunkedCookieHandler>` élément enfant et définition de sa `chunkSize` attribut.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="8b8d1-131">Si le `<chunkedCookieHandler>` élément n’est pas présent, la taille de segment par défaut de 2 000 octets est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="8b8d1-132">Cet élément ne peut pas être spécifié quand le `mode` attribut est défini sur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="8b8d1-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="8b8d1-133">Le `<chunkedCookieHandler>` élément est représenté par la <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> classe.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8d1-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b8d1-134">Example</span></span>  
 <span data-ttu-id="8b8d1-135">L’exemple suivant configure un gestionnaire de cookie mémorisé en bloc qui écrit des cookies par segments de 3 000 octets.</span><span class="sxs-lookup"><span data-stu-id="8b8d1-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b8d1-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b8d1-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
