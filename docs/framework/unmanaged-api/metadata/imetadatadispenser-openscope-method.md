---
title: "IMetaDataDispenser::OpenScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="e8d93-102">IMetaDataDispenser::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="e8d93-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="e8d93-103">Ouvre un fichier sur disque existant et mappe ses métadonnées dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e8d93-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8d93-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8d93-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8d93-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="e8d93-106">[in] Le nom du fichier à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="e8d93-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="e8d93-107">Le fichier doit contenir des métadonnées du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e8d93-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e8d93-108">[in] Une valeur de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération pour spécifier le mode (lecture, écriture et ainsi de suite) pour l’ouverture.</span><span class="sxs-lookup"><span data-stu-id="e8d93-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="e8d93-109">[in] L’IID de l’interface de métadonnées souhaitée doit être retourné ; l’appelant utilise l’interface pour importer (lecture) ou émettre des métadonnées de (écriture).</span><span class="sxs-lookup"><span data-stu-id="e8d93-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="e8d93-110">La valeur de `riid` doit spécifier l’une des interfaces « importation » ou « émission ».</span><span class="sxs-lookup"><span data-stu-id="e8d93-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="e8d93-111">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="e8d93-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e8d93-112">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="e8d93-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8d93-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8d93-113">Remarks</span></span>  
 <span data-ttu-id="e8d93-114">La copie en mémoire des métadonnées peut être interrogée à l’aide des méthodes à partir d’une des interfaces « importation », ou ajouté à l’aide des méthodes de l’une des interfaces « émission ».</span><span class="sxs-lookup"><span data-stu-id="e8d93-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="e8d93-115">Si le fichier cible ne contient pas de métadonnées CLR, la `OpenScope` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="e8d93-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="e8d93-116">Dans le .NET Framework version 1.0 et 1.1, si une étendue est ouvert avec `dwOpenFlags` défini sur ofRead, elle est éligible pour le partage.</span><span class="sxs-lookup"><span data-stu-id="e8d93-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="e8d93-117">Autrement dit, si suivantes des appels à `OpenScope` passez-lui le nom d’un fichier qui a été ouverte précédemment, la portée existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé.</span><span class="sxs-lookup"><span data-stu-id="e8d93-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="e8d93-118">Toutefois, des problèmes peuvent survenir en raison de ce partage.</span><span class="sxs-lookup"><span data-stu-id="e8d93-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="e8d93-119">Dans le .NET Framework version 2.0, les portées ouvertes avec `dwOpenFlags` défini sur ofRead ne sont plus partagées.</span><span class="sxs-lookup"><span data-stu-id="e8d93-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="e8d93-120">Utilisez la valeur ofReadOnly pour autoriser l’étendue à partager.</span><span class="sxs-lookup"><span data-stu-id="e8d93-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="e8d93-121">Lorsqu’une étendue est partagée, les requêtes qui utilisent « lecture/écriture » des interfaces de métadonnées échoue.</span><span class="sxs-lookup"><span data-stu-id="e8d93-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d93-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8d93-122">Requirements</span></span>  
 <span data-ttu-id="e8d93-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8d93-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8d93-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8d93-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8d93-125">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8d93-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8d93-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8d93-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d93-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8d93-127">See Also</span></span>  
 [<span data-ttu-id="e8d93-128">IMetaDataDispenser (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="e8d93-129">IMetaDataDispenserEx (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="e8d93-130">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="e8d93-131">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="e8d93-132">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e8d93-133">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="e8d93-134">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e8d93-135">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8d93-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
