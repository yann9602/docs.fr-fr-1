---
title: IMetaDataDispenser, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser
helpviewer_keywords: IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 678796357b36beb26ebbf34edc713ff6f15a7c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="d836c-102">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="d836c-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="d836c-103">Fournit des méthodes pour créer une nouvelle portée de métadonnées ou ouvrez-en une existante.</span><span class="sxs-lookup"><span data-stu-id="d836c-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d836c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d836c-104">Methods</span></span>  
  
|<span data-ttu-id="d836c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d836c-105">Method</span></span>|<span data-ttu-id="d836c-106">Description</span><span class="sxs-lookup"><span data-stu-id="d836c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d836c-107">DefineScope, méthode</span><span class="sxs-lookup"><span data-stu-id="d836c-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="d836c-108">Crée une nouvelle zone de mémoire où vous pouvez créer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d836c-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="d836c-109">OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="d836c-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="d836c-110">Ouvre un fichier sur disque existant et mappe ses métadonnées dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d836c-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="d836c-111">OpenScopeOnMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="d836c-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="d836c-112">Ouvre une zone de mémoire qui contient les métadonnées existantes.</span><span class="sxs-lookup"><span data-stu-id="d836c-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="d836c-113">Autrement dit, cette méthode ouvre une zone de mémoire dans lequel les données existantes sont traitées en tant que métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d836c-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d836c-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d836c-114">Requirements</span></span>  
 <span data-ttu-id="d836c-115">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d836c-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d836c-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d836c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d836c-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d836c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d836c-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d836c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d836c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d836c-119">See Also</span></span>  
 [<span data-ttu-id="d836c-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="d836c-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="d836c-121">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="d836c-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
