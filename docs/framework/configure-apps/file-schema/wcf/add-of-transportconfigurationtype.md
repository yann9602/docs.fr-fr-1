---
title: '&lt;add&gt; de &lt;transportConfigurationType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb00a5d5a2b4f64cdce6832faef4822b63f426d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="6c871-102">&lt;add&gt; de &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="6c871-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="6c871-103">Cet élément est une paire clé/valeur, qui identifie le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="6c871-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="6c871-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6c871-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c871-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="6c871-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="6c871-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="6c871-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="6c871-107">\<add></span><span class="sxs-lookup"><span data-stu-id="6c871-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c871-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c871-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c871-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6c871-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c871-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6c871-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c871-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="6c871-111">Attributes</span></span>  
  
|<span data-ttu-id="6c871-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="6c871-112">Attribute</span></span>|<span data-ttu-id="6c871-113">Description</span><span class="sxs-lookup"><span data-stu-id="6c871-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c871-114">name</span><span class="sxs-lookup"><span data-stu-id="6c871-114">name</span></span>|<span data-ttu-id="6c871-115">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="6c871-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="6c871-116">Contient une clé définie par l'utilisateur qui identifie uniquement le type de transport.</span><span class="sxs-lookup"><span data-stu-id="6c871-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="6c871-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="6c871-117">transportConfigurationType</span></span>|<span data-ttu-id="6c871-118">Chaîne contenant le type qui implémente le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="6c871-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c871-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6c871-119">Child Elements</span></span>  
 <span data-ttu-id="6c871-120">None</span><span class="sxs-lookup"><span data-stu-id="6c871-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c871-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6c871-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6c871-122">Élément</span><span class="sxs-lookup"><span data-stu-id="6c871-122">Element</span></span>|<span data-ttu-id="6c871-123">Description</span><span class="sxs-lookup"><span data-stu-id="6c871-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c871-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="6c871-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="6c871-125">Collection de types implémentant le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="6c871-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c871-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c871-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c871-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c871-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="6c871-128">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="6c871-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
