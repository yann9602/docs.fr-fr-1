---
title: "ICLRDataTarget::GetImageBase, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetImageBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 504c3ce7115cbab11d0510eaa2ebb0fdd9f1888b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="33de4-102">ICLRDataTarget::GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="33de4-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="33de4-103">Obtient l’adresse mémoire de base de l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="33de4-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33de4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33de4-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33de4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33de4-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="33de4-106">[in] Le nom de fichier de l’image, y compris son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="33de4-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="33de4-107">[out] Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="33de4-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33de4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="33de4-108">Remarks</span></span>  
 <span data-ttu-id="33de4-109">Le nom du fichier image peut ou ne peut pas avoir un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="33de4-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="33de4-110">Si un chemin d’accès est spécifié, la mise en correspondance est effectuée sur le chemin d’accès complet ; dans le cas contraire, la correspondance est effectuée uniquement sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="33de4-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33de4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="33de4-111">Requirements</span></span>  
 <span data-ttu-id="33de4-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33de4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33de4-113">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="33de4-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="33de4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33de4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33de4-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33de4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33de4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33de4-116">See Also</span></span>  
 [<span data-ttu-id="33de4-117">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="33de4-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
