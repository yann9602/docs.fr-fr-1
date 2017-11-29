---
title: "Méthode ICLRStrongName::StrongNameGetBlobFromImage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80edfa333f73854869c3fa6786e038c796b09087
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="e8743-102">Méthode ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="e8743-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="e8743-103">Obtient une représentation binaire de l’image d’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e8743-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8743-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8743-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8743-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8743-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="e8743-106">[in] Adresse mémoire du manifeste d’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="e8743-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e8743-107">[in] La taille, en octets, de l’image à `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="e8743-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="e8743-108">[in] Une mémoire tampon pour contenir la représentation binaire de l’image.</span><span class="sxs-lookup"><span data-stu-id="e8743-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="e8743-109">[dans, out] La taille maximale, en octets, demandée `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="e8743-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="e8743-110">Au retour, la taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="e8743-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8743-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e8743-111">Return Value</span></span>  
 <span data-ttu-id="e8743-112">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="e8743-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8743-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8743-113">Requirements</span></span>  
 <span data-ttu-id="e8743-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8743-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8743-115">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e8743-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e8743-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8743-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8743-117">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8743-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8743-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8743-118">See Also</span></span>  
 [<span data-ttu-id="e8743-119">StrongNameGetBlob (méthode)</span><span class="sxs-lookup"><span data-stu-id="e8743-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="e8743-120">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="e8743-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
