---
title: "Méthode ICLRStrongName::StrongNameSignatureVerification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e326eadcf91fbab0edb81844172bfabbd0851dc7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="c9efe-102">Méthode ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="c9efe-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="c9efe-103">Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c9efe-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9efe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9efe-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9efe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9efe-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c9efe-106">[in] Le chemin d’accès pour le fichier exécutable portable (.dll ou .exe) pour l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="c9efe-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="c9efe-107">[in] Indicateurs pour modifier le comportement de vérification.</span><span class="sxs-lookup"><span data-stu-id="c9efe-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="c9efe-108">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="c9efe-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="c9efe-109">`SN_INFLAG_FORCE_VER`(0 x 00000001) - force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="c9efe-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="c9efe-110">`SN_INFLAG_INSTALL`(0 x 00000002) - Spécifie qu’il s’agit de la première fois que le manifeste est vérifié.</span><span class="sxs-lookup"><span data-stu-id="c9efe-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="c9efe-111">`SN_INFLAG_ADMIN_ACCESS`(0 x 00000004) - Spécifie que le cache autorise l’accès uniquement aux utilisateurs qui ont des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="c9efe-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="c9efe-112">`SN_INFLAG_USER_ACCESS`(0 x 00000008) - Spécifie que l’assembly est accessible uniquement à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c9efe-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="c9efe-113">`SN_INFLAG_ALL_ACCESS`(0 x 00000010) - Spécifie que le cache ne va fournir aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="c9efe-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="c9efe-114">`SN_INFLAG_RUNTIME`(0 x 80000000) - réservé pour le débogage interne.</span><span class="sxs-lookup"><span data-stu-id="c9efe-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="c9efe-115">[out] Indicateurs qui indique si la signature de nom fort a été vérifiée.</span><span class="sxs-lookup"><span data-stu-id="c9efe-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="c9efe-116">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="c9efe-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="c9efe-117">`SN_OUTFLAG_WAS_VERIFIED`(0 x 00000001) - cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres de Registre.</span><span class="sxs-lookup"><span data-stu-id="c9efe-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9efe-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9efe-118">Return Value</span></span>  
 <span data-ttu-id="c9efe-119">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="c9efe-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9efe-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9efe-120">Requirements</span></span>  
 <span data-ttu-id="c9efe-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9efe-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9efe-122">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c9efe-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9efe-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9efe-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9efe-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9efe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9efe-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9efe-125">See Also</span></span>  
 [<span data-ttu-id="c9efe-126">StrongNameSignatureVerificationEx (méthode)</span><span class="sxs-lookup"><span data-stu-id="c9efe-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="c9efe-127">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="c9efe-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
