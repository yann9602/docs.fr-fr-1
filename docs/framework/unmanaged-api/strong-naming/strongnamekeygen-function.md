---
title: StrongNameKeyGen, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGen
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGen
helpviewer_keywords: StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3bb9530884f61345d439ec8662a088e1d152de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="dee0e-102">StrongNameKeyGen, fonction</span><span class="sxs-lookup"><span data-stu-id="dee0e-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="dee0e-103">Crée une nouvelle paire de clés publique/privée pour l’utiliser avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="dee0e-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="dee0e-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-104">This function has been deprecated.</span></span> <span data-ttu-id="dee0e-105">Utilisez le [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="dee0e-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee0e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dee0e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dee0e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dee0e-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="dee0e-108">[in] Le nom du conteneur de clé demandé.</span><span class="sxs-lookup"><span data-stu-id="dee0e-108">[in] The requested key container name.</span></span> <span data-ttu-id="dee0e-109">`wszKeyContainer`doit être une chaîne vide ou null pour générer un nom temporaire.</span><span class="sxs-lookup"><span data-stu-id="dee0e-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dee0e-110">[in] Spécifie s’il faut laisser la clé enregistrée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="dee0e-111">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="dee0e-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="dee0e-112">0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.</span><span class="sxs-lookup"><span data-stu-id="dee0e-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="dee0e-113">0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit rester enregistrée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="dee0e-114">[out] La paire de clés publique/privée retournée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="dee0e-115">[out] La taille, en octets, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="dee0e-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dee0e-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dee0e-116">Return Value</span></span>  
 <span data-ttu-id="dee0e-117">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="dee0e-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dee0e-118">Notes</span><span class="sxs-lookup"><span data-stu-id="dee0e-118">Remarks</span></span>  
 <span data-ttu-id="dee0e-119">Le `StrongNameKeyGen` fonction crée une clé 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="dee0e-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="dee0e-120">Une fois la clé est récupérée, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) afin de libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="dee0e-121">Si le `StrongNameKeyGen` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="dee0e-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee0e-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dee0e-122">Requirements</span></span>  
 <span data-ttu-id="dee0e-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee0e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee0e-124">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dee0e-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dee0e-125">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dee0e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dee0e-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee0e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee0e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dee0e-127">See Also</span></span>  
 [<span data-ttu-id="dee0e-128">StrongNameKeyGen, méthode</span><span class="sxs-lookup"><span data-stu-id="dee0e-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="dee0e-129">StrongNameKeyGenEx, méthode</span><span class="sxs-lookup"><span data-stu-id="dee0e-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="dee0e-130">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="dee0e-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
