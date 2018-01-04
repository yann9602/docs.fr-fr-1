---
title: CreateAssemblyNameObject, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyNameObject
helpviewer_keywords: CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d2616bd7aee878ebbc1d196cb1ac5f90ae7bd04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="4ad79-102">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="4ad79-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="4ad79-103">Obtient un pointeur d’interface vers un [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance qui représente l’identité unique de l’assembly avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4ad79-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad79-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ad79-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4ad79-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="4ad79-106">[out] Retourné `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="4ad79-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="4ad79-107">[in] Le nom de l’assembly pour lequel créer le nouveau `IAssemblyName` instance.</span><span class="sxs-lookup"><span data-stu-id="4ad79-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4ad79-108">[in] Indicateurs à passer au constructeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="4ad79-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4ad79-109">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="4ad79-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4ad79-110">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="4ad79-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad79-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ad79-111">Requirements</span></span>  
 <span data-ttu-id="4ad79-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ad79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad79-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4ad79-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4ad79-114">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ad79-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ad79-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad79-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ad79-116">See Also</span></span>  
 [<span data-ttu-id="4ad79-117">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="4ad79-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="4ad79-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="4ad79-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
