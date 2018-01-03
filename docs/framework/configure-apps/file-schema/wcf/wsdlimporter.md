---
title: '&lt;wsdlImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc85c93dc73918d661195e33ce5094622db36af4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="a4499-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="a4499-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="a4499-103">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="a4499-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="a4499-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a4499-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4499-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="a4499-105">\<client></span></span>  
<span data-ttu-id="a4499-106">\<métadonnées ></span><span class="sxs-lookup"><span data-stu-id="a4499-106">\<metadata></span></span>  
<span data-ttu-id="a4499-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="a4499-107">\<wsdlImporters></span></span>  
<span data-ttu-id="a4499-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="a4499-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4499-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4499-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4499-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4499-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4499-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a4499-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4499-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4499-112">Attributes</span></span>  
  
|<span data-ttu-id="a4499-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a4499-113">Attribute</span></span>|<span data-ttu-id="a4499-114">Description</span><span class="sxs-lookup"><span data-stu-id="a4499-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a4499-115">Type de cet élément.</span><span class="sxs-lookup"><span data-stu-id="a4499-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4499-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4499-116">Child Elements</span></span>  
 <span data-ttu-id="a4499-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4499-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4499-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4499-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a4499-119">Élément</span><span class="sxs-lookup"><span data-stu-id="a4499-119">Element</span></span>|<span data-ttu-id="a4499-120">Description</span><span class="sxs-lookup"><span data-stu-id="a4499-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4499-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="a4499-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="a4499-122">Indique tous les importateurs WSDL qui importent des métadonnées WSDL (Web Services Description Language) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="a4499-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4499-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a4499-123">Remarks</span></span>  
 <span data-ttu-id="a4499-124">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a4499-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="a4499-125">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="a4499-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="a4499-126">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="a4499-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4499-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4499-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="a4499-128">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="a4499-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="a4499-129">Clients</span><span class="sxs-lookup"><span data-stu-id="a4499-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
