---
title: "IMetaDataEmit::SetPinvokeMap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="6c0cb-102">IMetaDataEmit::SetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="6c0cb-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="6c0cb-103">Définit ou modifie les fonctionnalités de la signature PInvoke d’une méthode définie par un appel antérieur à [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="6c0cb-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c0cb-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c0cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c0cb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6c0cb-106">[in] Le `mdToken` que le mappage s’applique plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="6c0cb-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="6c0cb-107">[in] Indicateurs utilisés par PInvoke pour effectuer le mappage.</span><span class="sxs-lookup"><span data-stu-id="6c0cb-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="6c0cb-108">Il s’agit d’un masque de bits de `CorPinvokeMap` valeurs.</span><span class="sxs-lookup"><span data-stu-id="6c0cb-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="6c0cb-109">[in] Le nom de l’exportation de la cible de la DLL native.</span><span class="sxs-lookup"><span data-stu-id="6c0cb-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="6c0cb-110">[in] Le `mdModuleRef` jeton pour la cible de DLL non managée.</span><span class="sxs-lookup"><span data-stu-id="6c0cb-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0cb-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6c0cb-111">Requirements</span></span>  
 <span data-ttu-id="6c0cb-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0cb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0cb-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c0cb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c0cb-114">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c0cb-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c0cb-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0cb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0cb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c0cb-116">See Also</span></span>  
 [<span data-ttu-id="6c0cb-117">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="6c0cb-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6c0cb-118">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="6c0cb-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
