---
title: "Méthode ICLRStrongName::StrongNameKeyGenEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a303dd65cd366936d060f96899d5e218eeec9d7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="6ee90-102">Méthode ICLRStrongName::StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="6ee90-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="6ee90-103">Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour l’utiliser avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="6ee90-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ee90-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ee90-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6ee90-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="6ee90-106">[in] Le nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="6ee90-106">[in] The requested key container name.</span></span> <span data-ttu-id="6ee90-107">`wszKeyContainer`doit être une chaîne non vide ou la valeur null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="6ee90-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6ee90-108">[in] Une valeur qui spécifie s’il faut laisser la clé enregistrée.</span><span class="sxs-lookup"><span data-stu-id="6ee90-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="6ee90-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="6ee90-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="6ee90-110">0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="6ee90-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="6ee90-111">0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit rester enregistrée.</span><span class="sxs-lookup"><span data-stu-id="6ee90-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="6ee90-112">[in] La taille demandée de la clé, en bits.</span><span class="sxs-lookup"><span data-stu-id="6ee90-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="6ee90-113">[out] La paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="6ee90-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="6ee90-114">[out] La taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="6ee90-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ee90-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6ee90-115">Return Value</span></span>  
 <span data-ttu-id="6ee90-116">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="6ee90-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ee90-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ee90-117">Remarks</span></span>  
 <span data-ttu-id="6ee90-118">Les versions de .NET Framework 1.0 et 1.1 requièrent un `dwKeySize` de 1 024 bits pour signer un assembly avec un nom fort ; version 2.0 ajoute la prise en charge de clés 2 048 bits.</span><span class="sxs-lookup"><span data-stu-id="6ee90-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="6ee90-119">Une fois la clé est récupérée, vous devez appeler la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="6ee90-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee90-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ee90-120">Requirements</span></span>  
 <span data-ttu-id="6ee90-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee90-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee90-122">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6ee90-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6ee90-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ee90-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ee90-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee90-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee90-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ee90-125">See Also</span></span>  
 [<span data-ttu-id="6ee90-126">StrongNameKeyGen (méthode)</span><span class="sxs-lookup"><span data-stu-id="6ee90-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="6ee90-127">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="6ee90-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
