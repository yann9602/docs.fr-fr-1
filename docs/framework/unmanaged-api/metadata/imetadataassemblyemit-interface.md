---
title: IMetaDataAssemblyEmit, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a7e4bd68bfd985b8902ae3b2340773ca77eee10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="8b38a-102">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8b38a-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="8b38a-103">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="8b38a-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b38a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8b38a-104">Methods</span></span>  
  
|<span data-ttu-id="8b38a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-105">Method</span></span>|<span data-ttu-id="8b38a-106">Description</span><span class="sxs-lookup"><span data-stu-id="8b38a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b38a-107">DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="8b38a-108">Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="8b38a-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8b38a-109">DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="8b38a-110">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="8b38a-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8b38a-111">DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="8b38a-112">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="8b38a-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8b38a-113">DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="8b38a-114">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="8b38a-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8b38a-115">DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="8b38a-116">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="8b38a-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8b38a-117">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="8b38a-118">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b38a-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="8b38a-119">SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="8b38a-120">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b38a-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="8b38a-121">SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="8b38a-122">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b38a-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="8b38a-123">SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="8b38a-124">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b38a-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="8b38a-125">SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b38a-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="8b38a-126">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8b38a-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b38a-127">Notes</span><span class="sxs-lookup"><span data-stu-id="8b38a-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b38a-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8b38a-128">Requirements</span></span>  
 <span data-ttu-id="8b38a-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b38a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b38a-130">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b38a-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b38a-131">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b38a-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b38a-132">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b38a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b38a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b38a-133">See Also</span></span>  
 [<span data-ttu-id="8b38a-134">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8b38a-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="8b38a-135">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="8b38a-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
