---
title: "ICLRMetadataLocator::GetMetadata, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator.GetMetadata
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="ac108-102">ICLRMetadataLocator::GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="ac108-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="ac108-103">Appelé par les services d’accès aux données du common language runtime (CLR) pour récupérer les métadonnées d’une image.</span><span class="sxs-lookup"><span data-stu-id="ac108-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac108-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac108-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac108-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac108-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="ac108-106">[in] Chaîne qui spécifie le chemin d’accès du fichier image.</span><span class="sxs-lookup"><span data-stu-id="ac108-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="ac108-107">[in] L’horodatage du fichier image.</span><span class="sxs-lookup"><span data-stu-id="ac108-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="ac108-108">[in] La taille du fichier image.</span><span class="sxs-lookup"><span data-stu-id="ac108-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="ac108-109">[in] L’identificateur global unique de l’image.</span><span class="sxs-lookup"><span data-stu-id="ac108-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="ac108-110">[in] L’adresse virtuelle relative (RVA) des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ac108-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="ac108-111">L’adresse est relatif à l’adresse de base d’image.</span><span class="sxs-lookup"><span data-stu-id="ac108-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="ac108-112">[in] Réservé à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ac108-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="ac108-113">[in] La taille de la mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ac108-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ac108-114">[out] La mémoire tampon dans laquelle placer les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ac108-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="ac108-115">[out] La taille des métadonnées qui sont retournée.</span><span class="sxs-lookup"><span data-stu-id="ac108-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac108-116">Notes</span><span class="sxs-lookup"><span data-stu-id="ac108-116">Remarks</span></span>  
 <span data-ttu-id="ac108-117">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="ac108-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac108-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac108-118">Requirements</span></span>  
 <span data-ttu-id="ac108-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac108-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac108-120">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ac108-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ac108-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac108-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac108-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac108-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac108-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac108-123">See Also</span></span>  
 [<span data-ttu-id="ac108-124">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="ac108-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
