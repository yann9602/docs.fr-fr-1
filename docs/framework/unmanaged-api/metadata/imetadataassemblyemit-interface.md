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
ms.openlocfilehash: af7a5fd5a564aa7366924f47b0c526aff7153521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="34ab3-102">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="34ab3-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="34ab3-103">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="34ab3-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34ab3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="34ab3-104">Methods</span></span>  
  
|<span data-ttu-id="34ab3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="34ab3-105">Method</span></span>|<span data-ttu-id="34ab3-106">Description</span><span class="sxs-lookup"><span data-stu-id="34ab3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34ab3-107">DefineAssembly (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="34ab3-108">Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="34ab3-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="34ab3-109">DefineAssemblyRef (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="34ab3-110">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="34ab3-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="34ab3-111">DefineExportedType (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="34ab3-112">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="34ab3-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="34ab3-113">DefineFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="34ab3-114">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="34ab3-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="34ab3-115">DefineManifestResource (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="34ab3-116">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="34ab3-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="34ab3-117">SetAssemblyProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="34ab3-118">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34ab3-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="34ab3-119">SetAssemblyRefProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="34ab3-120">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34ab3-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="34ab3-121">SetExportedTypeProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="34ab3-122">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34ab3-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="34ab3-123">SetFileProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="34ab3-124">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34ab3-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="34ab3-125">SetManifestResourceProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="34ab3-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="34ab3-126">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34ab3-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34ab3-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="34ab3-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34ab3-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="34ab3-128">Requirements</span></span>  
 <span data-ttu-id="34ab3-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34ab3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34ab3-130">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="34ab3-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34ab3-131">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34ab3-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34ab3-132">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34ab3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ab3-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34ab3-133">See Also</span></span>  
 [<span data-ttu-id="34ab3-134">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="34ab3-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="34ab3-135">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="34ab3-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
