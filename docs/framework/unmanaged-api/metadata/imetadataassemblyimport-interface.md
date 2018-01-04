---
title: IMetaDataAssemblyImport, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 992b588d16bc221f6b72044da40d09fbb6894511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="7374b-102">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="7374b-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="7374b-103">Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.</span><span class="sxs-lookup"><span data-stu-id="7374b-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7374b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7374b-104">Methods</span></span>  
  
|<span data-ttu-id="7374b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-105">Method</span></span>|<span data-ttu-id="7374b-106">Description</span><span class="sxs-lookup"><span data-stu-id="7374b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7374b-107">CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="7374b-108">Libère le handle à l’énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="7374b-109">EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="7374b-110">Obtient un pointeur d’interface vers un énumérateur qui contient le `mdAssemblyRef` jetons des assemblys référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="7374b-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="7374b-111">EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="7374b-112">Obtient un pointeur d’interface vers un énumérateur qui contient le `mdExportedType` jetons des types COM référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="7374b-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="7374b-113">EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="7374b-114">Obtient un pointeur d’interface vers un énumérateur qui contient le `mdFile` jetons des fichiers référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="7374b-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="7374b-115">EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="7374b-116">Obtient un pointeur d’interface vers un énumérateur qui contient le `mdManifestResource` jetons des ressources référencées par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="7374b-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="7374b-117">FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="7374b-118">Obtient un tableau de `mdAssemblyRef` jetons pour les assemblys avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="7374b-119">FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="7374b-120">Obtient un `mdExportedType` jeton pour le type COM avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="7374b-121">FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="7374b-122">Obtient un `mdManifestResource` jeton pour la ressource avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="7374b-123">GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="7374b-124">Obtient le jeton pour l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="7374b-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="7374b-125">GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="7374b-126">Obtient les paramètres de propriété de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="7374b-127">GetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="7374b-128">Obtient les paramètres de propriété spécifié `mdAssemblyRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="7374b-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="7374b-129">GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="7374b-130">Obtient les paramètres de propriété du type COM spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="7374b-131">GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="7374b-132">Obtient les paramètres de propriété du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7374b-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="7374b-133">GetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7374b-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="7374b-134">Obtient les paramètres de propriété de la ressource de manifeste spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7374b-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7374b-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7374b-135">Requirements</span></span>  
 <span data-ttu-id="7374b-136">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7374b-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7374b-137">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7374b-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7374b-138">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7374b-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7374b-139">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7374b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7374b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7374b-140">See Also</span></span>  
 [<span data-ttu-id="7374b-141">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="7374b-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="7374b-142">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7374b-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
