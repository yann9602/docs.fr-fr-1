---
title: IMetaDataDispenserEx, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="4bca2-102">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="4bca2-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="4bca2-103">Étend la [IMetaDataDispenser (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface afin de permettre à contrôlent le fonctionnement de l’API de métadonnées sur la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4bca2-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bca2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4bca2-104">Methods</span></span>  
  
|<span data-ttu-id="4bca2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-105">Method</span></span>|<span data-ttu-id="4bca2-106">Description</span><span class="sxs-lookup"><span data-stu-id="4bca2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bca2-107">FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="4bca2-108">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="4bca2-108">This method is not implemented.</span></span> <span data-ttu-id="4bca2-109">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4bca2-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bca2-110">FindAssemblyModule, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="4bca2-111">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="4bca2-111">This method is not implemented.</span></span> <span data-ttu-id="4bca2-112">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4bca2-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bca2-113">GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="4bca2-114">Obtient le répertoire qui contient le common language runtime (CLR) actuel.</span><span class="sxs-lookup"><span data-stu-id="4bca2-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="4bca2-115">Cette méthode est prise en charge uniquement pour une utilisation par les débogueurs out-of-process.</span><span class="sxs-lookup"><span data-stu-id="4bca2-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="4bca2-116">Si elle est appelée à partir d’un autre composant, elle retournera E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4bca2-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bca2-117">GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="4bca2-118">Obtient la valeur de l’option spécifiée pour la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4bca2-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="4bca2-119">L’option contrôle la gestion des appels à la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4bca2-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="4bca2-120">OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="4bca2-121">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="4bca2-121">This method is not implemented.</span></span> <span data-ttu-id="4bca2-122">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4bca2-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="4bca2-123">SetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="4bca2-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="4bca2-124">Définit l’option spécifiée à une valeur donnée pour la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4bca2-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="4bca2-125">L’option contrôle la gestion des appels à la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4bca2-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bca2-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4bca2-126">Requirements</span></span>  
 <span data-ttu-id="4bca2-127">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bca2-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bca2-128">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bca2-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bca2-129">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4bca2-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bca2-130">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bca2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bca2-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bca2-131">See Also</span></span>  
 [<span data-ttu-id="4bca2-132">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="4bca2-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="4bca2-133">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="4bca2-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="4bca2-134">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4bca2-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4bca2-135">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4bca2-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
