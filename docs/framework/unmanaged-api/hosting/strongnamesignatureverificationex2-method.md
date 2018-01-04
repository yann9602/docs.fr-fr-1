---
title: "StrongNameSignatureVerificationEx2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4faa7fee32d9cab5a75772f29d2014473e2bee0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="558d7-102">StrongNameSignatureVerificationEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="558d7-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="558d7-103">Vérifie la signature d’un assembly portant un nom fort et fournit un mappage à partir de la clé ECMA à une clé réelle.</span><span class="sxs-lookup"><span data-stu-id="558d7-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="558d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="558d7-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="558d7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="558d7-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="558d7-106">[in] Le chemin d’accès pour le fichier exécutable portable (.exe ou .dll) pour l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="558d7-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="558d7-107">[in] `true` pour effectuer la vérification, même s’il est nécessaire de remplacer les paramètres de Registre ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="558d7-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="558d7-108">[in] Un pointeur vers le mappage à partir de la clé publique ECMA à la clé réelle utilisée pour la vérification.</span><span class="sxs-lookup"><span data-stu-id="558d7-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="558d7-109">[in] La longueur de la clé publique ECMA réelle.</span><span class="sxs-lookup"><span data-stu-id="558d7-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="558d7-110">[out] `true` si la signature de nom fort a été vérifiée ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="558d7-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="558d7-111">Ce paramètre est également défini sur `false` si la vérification a réussi en raison des paramètres de Registre.</span><span class="sxs-lookup"><span data-stu-id="558d7-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="558d7-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="558d7-112">Return Value</span></span>  
 <span data-ttu-id="558d7-113">`S_OK`Si la vérification a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="558d7-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="558d7-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="558d7-114">Requirements</span></span>  
 <span data-ttu-id="558d7-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="558d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="558d7-116">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="558d7-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="558d7-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="558d7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="558d7-118">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="558d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558d7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="558d7-119">See Also</span></span>  
 [<span data-ttu-id="558d7-120">StrongNameSignatureVerification, méthode</span><span class="sxs-lookup"><span data-stu-id="558d7-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="558d7-121">StrongNameSignatureVerificationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="558d7-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="558d7-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="558d7-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
