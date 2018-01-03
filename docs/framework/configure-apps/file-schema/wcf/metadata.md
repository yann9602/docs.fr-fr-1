---
title: "&lt;métadonnées&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1da05ebd48a3fff7c35510db4093d56831a8fcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmetadatagt"></a><span data-ttu-id="d86be-102">&lt;métadonnées&gt;</span><span class="sxs-lookup"><span data-stu-id="d86be-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="d86be-103">Indique la façon dont les métadonnées peuvent être traitées.</span><span class="sxs-lookup"><span data-stu-id="d86be-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="d86be-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d86be-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d86be-105">\<client ></span><span class="sxs-lookup"><span data-stu-id="d86be-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d86be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d86be-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d86be-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d86be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d86be-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d86be-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d86be-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="d86be-109">Attributes</span></span>  
 <span data-ttu-id="d86be-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d86be-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d86be-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d86be-111">Child Elements</span></span>  
  
|<span data-ttu-id="d86be-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d86be-112">Element</span></span>|<span data-ttu-id="d86be-113">Description</span><span class="sxs-lookup"><span data-stu-id="d86be-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d86be-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="d86be-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="d86be-115">Indique tous les importateurs de stratégie contrôlant l’importation d’assertions de stratégie personnalisées concernant les liaisons.</span><span class="sxs-lookup"><span data-stu-id="d86be-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="d86be-116">Un importateur de stratégie permet de rechercher des assertions de stratégie personnalisées concernant les fonctionnalités de liaison et de joindre un élément de liaison personnalisé qui implémente les fonctionnalités requises par l’assertion.</span><span class="sxs-lookup"><span data-stu-id="d86be-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="d86be-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="d86be-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="d86be-118">Indique tous les importateurs WSDL qui importent des métadonnées Web Services Description Language (WSDL) 1.1 avec des pièces jointes WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="d86be-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="d86be-119">Un importateur WSDL permet d'importer des métadonnées et de convertir ces informations en différentes classes représentant les informations de contrat et de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d86be-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="d86be-120">Il peut importer sélectivement des informations de contrat et de point de terminaison ainsi que des propriétés qui exposent toute erreur d'importation et accepte des informations de types liées au processus d'importation et de conversion.</span><span class="sxs-lookup"><span data-stu-id="d86be-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="d86be-121">Il prend également en charge les informations et les propriétés de liaison qui donnent accès aux documents de stratégie, documents WSDL, extensions WSDL et documents de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="d86be-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d86be-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d86be-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d86be-123">Élément</span><span class="sxs-lookup"><span data-stu-id="d86be-123">Element</span></span>|<span data-ttu-id="d86be-124">Description</span><span class="sxs-lookup"><span data-stu-id="d86be-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d86be-125">\<client ></span><span class="sxs-lookup"><span data-stu-id="d86be-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="d86be-126">La section client définit la liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="d86be-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d86be-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d86be-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="d86be-128">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="d86be-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="d86be-129">Clients</span><span class="sxs-lookup"><span data-stu-id="d86be-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
