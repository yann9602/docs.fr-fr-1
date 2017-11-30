---
title: '&lt;client&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="7b2b8-102">&lt;client&gt;</span><span class="sxs-lookup"><span data-stu-id="7b2b8-102">&lt;client&gt;</span></span>
<span data-ttu-id="7b2b8-103">L'élément `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="7b2b8-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7b2b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b2b8-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="7b2b8-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b2b8-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b2b8-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7b2b8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7b2b8-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b2b8-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7b2b8-109">Attributes</span></span>  
 <span data-ttu-id="7b2b8-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="7b2b8-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b2b8-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7b2b8-111">Child Elements</span></span>  
  
|<span data-ttu-id="7b2b8-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7b2b8-112">Element</span></span>|<span data-ttu-id="7b2b8-113">Description</span><span class="sxs-lookup"><span data-stu-id="7b2b8-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b2b8-114">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="7b2b8-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="7b2b8-115">Contient une collection d’éléments de point de terminaison qui spécifient les points de terminaison auxquels ce client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="7b2b8-116">\<métadonnées ></span><span class="sxs-lookup"><span data-stu-id="7b2b8-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="7b2b8-117">Contient des paramètres pour le traitement de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b2b8-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7b2b8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7b2b8-119">Élément</span><span class="sxs-lookup"><span data-stu-id="7b2b8-119">Element</span></span>|<span data-ttu-id="7b2b8-120">Description</span><span class="sxs-lookup"><span data-stu-id="7b2b8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b2b8-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7b2b8-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="7b2b8-122">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7b2b8-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b2b8-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b2b8-123">Remarks</span></span>  
 <span data-ttu-id="7b2b8-124">La section `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="7b2b8-125">Chaque point de terminaison répertorié dans la section client définit ses propres liaison, comportement et contrat.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="7b2b8-126">Il est identifié uniquement par la combinaison des attributs `name` et `contract`.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="7b2b8-127">Le code client spécifie le `name` permettant de se connecter à un point de terminaison pour le service que le client implémente.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="7b2b8-128">Si l'attribut `name` est omis, le point de terminaison agit comme point de terminaison par défaut pour le contrat qu'il implémente.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="7b2b8-129">De plus, cette section spécifie également des paramètres pour le traitement des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7b2b8-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b2b8-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b2b8-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b2b8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b2b8-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="7b2b8-132">Configuration du Client WCF</span><span class="sxs-lookup"><span data-stu-id="7b2b8-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="7b2b8-133">Clients</span><span class="sxs-lookup"><span data-stu-id="7b2b8-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
