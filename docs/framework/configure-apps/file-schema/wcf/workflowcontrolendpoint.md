---
title: '&lt;workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 741968e160683ab38f79effdfa0bdf56053cfb93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="32db8-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="32db8-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="32db8-103">Cet élément de configuration définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail (créer, exécuter, interrompre, arrêter, etc.).</span><span class="sxs-lookup"><span data-stu-id="32db8-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="32db8-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="32db8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32db8-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="32db8-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32db8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32db8-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32db8-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="32db8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="32db8-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="32db8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32db8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="32db8-109">Attributes</span></span>  
  
|<span data-ttu-id="32db8-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="32db8-110">Attribute</span></span>|<span data-ttu-id="32db8-111">Description</span><span class="sxs-lookup"><span data-stu-id="32db8-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32db8-112">name</span><span class="sxs-lookup"><span data-stu-id="32db8-112">name</span></span>|<span data-ttu-id="32db8-113">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="32db8-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="32db8-114">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="32db8-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32db8-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="32db8-115">Child Elements</span></span>  
 <span data-ttu-id="32db8-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="32db8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32db8-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="32db8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="32db8-118">Élément</span><span class="sxs-lookup"><span data-stu-id="32db8-118">Element</span></span>|<span data-ttu-id="32db8-119">Description</span><span class="sxs-lookup"><span data-stu-id="32db8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32db8-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="32db8-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="32db8-121">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="32db8-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32db8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32db8-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
