---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6eefecb696c88d160e56c7f12a1b03ea67e531b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="c8836-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="c8836-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="c8836-103">Cet élément de configuration définit un point de terminaison standard avec un contrat IMetadataExchange fixe.</span><span class="sxs-lookup"><span data-stu-id="c8836-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="c8836-104">Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.</span><span class="sxs-lookup"><span data-stu-id="c8836-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="c8836-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c8836-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8836-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c8836-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8836-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8836-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8836-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c8836-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c8836-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c8836-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8836-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c8836-110">Attributes</span></span>  
  
|<span data-ttu-id="c8836-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c8836-111">Attribute</span></span>|<span data-ttu-id="c8836-112">Description</span><span class="sxs-lookup"><span data-stu-id="c8836-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8836-113">name</span><span class="sxs-lookup"><span data-stu-id="c8836-113">name</span></span>|<span data-ttu-id="c8836-114">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="c8836-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="c8836-115">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="c8836-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8836-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c8836-116">Child Elements</span></span>  
 <span data-ttu-id="c8836-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c8836-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8836-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c8836-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c8836-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c8836-119">Element</span></span>|<span data-ttu-id="c8836-120">Description</span><span class="sxs-lookup"><span data-stu-id="c8836-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8836-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c8836-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c8836-122">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="c8836-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
