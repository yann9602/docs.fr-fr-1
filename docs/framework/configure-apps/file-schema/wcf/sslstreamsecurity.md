---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65233bf416080212a5c1447cffd329eca1b921f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="aaa0c-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="aaa0c-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="aaa0c-103">Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l’aide d’un flux SSL.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="aaa0c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="aaa0c-105">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-105">\<bindings></span></span>  
<span data-ttu-id="aaa0c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-106">\<customBinding></span></span>  
<span data-ttu-id="aaa0c-107">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-107">\<binding></span></span>  
<span data-ttu-id="aaa0c-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa0c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa0c-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaa0c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aaa0c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aaa0c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaa0c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="aaa0c-112">Attributes</span></span>  
  
|<span data-ttu-id="aaa0c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="aaa0c-113">Attribute</span></span>|<span data-ttu-id="aaa0c-114">Description</span><span class="sxs-lookup"><span data-stu-id="aaa0c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaa0c-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="aaa0c-115">requireClientCertificate</span></span>|<span data-ttu-id="aaa0c-116">Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="aaa0c-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-117">The default is `false`.</span></span>|  
|<span data-ttu-id="aaa0c-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="aaa0c-118">sslProtocols</span></span>|<span data-ttu-id="aaa0c-119">Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="aaa0c-120">La valeur par défaut est Ssl3 &#124; TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaa0c-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aaa0c-121">Child Elements</span></span>  
 <span data-ttu-id="aaa0c-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaa0c-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aaa0c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aaa0c-124">Élément</span><span class="sxs-lookup"><span data-stu-id="aaa0c-124">Element</span></span>|<span data-ttu-id="aaa0c-125">Description</span><span class="sxs-lookup"><span data-stu-id="aaa0c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaa0c-126">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="aaa0c-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="aaa0c-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aaa0c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaa0c-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="aaa0c-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="aaa0c-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="aaa0c-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="aaa0c-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="aaa0c-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="aaa0c-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="aaa0c-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aaa0c-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
