---
title: "ICorDebugAppDomain::GetModuleFromMetaDataInterface, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69b1d7d02031e23571a7a5d0e5c64e6bea66d636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="51742-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="51742-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="51742-103">Obtient le module qui correspond à l’interface de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51742-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51742-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51742-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51742-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51742-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="51742-106">[in] Un pointeur vers un objet qui est un de le [interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="51742-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="51742-107">[out] Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module correspondant à l’interface de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51742-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51742-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="51742-108">Requirements</span></span>  
 <span data-ttu-id="51742-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51742-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51742-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51742-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51742-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51742-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51742-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51742-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
