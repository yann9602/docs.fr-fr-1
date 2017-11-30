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
ms.openlocfilehash: 1d397995266d6063164510a4b563ba94f7f54950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="efafc-102">ICLRDataTarget::GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="efafc-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="efafc-103">Obtient l’adresse mémoire de base de l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="efafc-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efafc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efafc-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efafc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efafc-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="efafc-106">[in] Le nom de fichier de l’image, y compris son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="efafc-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="efafc-107">[out] Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.</span><span class="sxs-lookup"><span data-stu-id="efafc-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efafc-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="efafc-108">Remarks</span></span>  
 <span data-ttu-id="efafc-109">Le nom du fichier image peut ou ne peut pas avoir un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="efafc-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="efafc-110">Si un chemin d’accès est spécifié, la mise en correspondance est effectuée sur le chemin d’accès complet ; dans le cas contraire, la correspondance est effectuée uniquement sur le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="efafc-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efafc-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="efafc-111">Requirements</span></span>  
 <span data-ttu-id="efafc-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efafc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efafc-113">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="efafc-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="efafc-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efafc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efafc-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efafc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efafc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efafc-116">See Also</span></span>  
 [<span data-ttu-id="efafc-117">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="efafc-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
