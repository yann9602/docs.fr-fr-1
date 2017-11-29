---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b048b160f337897765fa4fcff73a4906534ab08b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="710e4-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="710e4-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="710e4-103">Représente une collection d’éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="710e4-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="710e4-104">Peut être utilisé pour ajouter des protocoles WAS personnalisés.</span><span class="sxs-lookup"><span data-stu-id="710e4-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="710e4-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="710e4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="710e4-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="710e4-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="710e4-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="710e4-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710e4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="710e4-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="710e4-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="710e4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="710e4-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="710e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="710e4-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="710e4-111">Attributes</span></span>  
  
|<span data-ttu-id="710e4-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="710e4-112">Attribute</span></span>|<span data-ttu-id="710e4-113">Description</span><span class="sxs-lookup"><span data-stu-id="710e4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="710e4-114">name</span><span class="sxs-lookup"><span data-stu-id="710e4-114">name</span></span>|<span data-ttu-id="710e4-115">Nom du transport.</span><span class="sxs-lookup"><span data-stu-id="710e4-115">The name of the transport</span></span>|  
|<span data-ttu-id="710e4-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="710e4-116">transportConfigurationType</span></span>|<span data-ttu-id="710e4-117">Type qui implémente le transport.</span><span class="sxs-lookup"><span data-stu-id="710e4-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="710e4-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="710e4-118">Child Elements</span></span>  
  
|<span data-ttu-id="710e4-119">Élément</span><span class="sxs-lookup"><span data-stu-id="710e4-119">Element</span></span>|<span data-ttu-id="710e4-120">Description</span><span class="sxs-lookup"><span data-stu-id="710e4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="710e4-121">\<add></span><span class="sxs-lookup"><span data-stu-id="710e4-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="710e4-122">Ajoute un élément de configuration identifiant le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="710e4-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="710e4-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="710e4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="710e4-124">Élément</span><span class="sxs-lookup"><span data-stu-id="710e4-124">Element</span></span>|<span data-ttu-id="710e4-125">Description</span><span class="sxs-lookup"><span data-stu-id="710e4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="710e4-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="710e4-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="710e4-127">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="710e4-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="710e4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="710e4-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="710e4-129">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="710e4-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
