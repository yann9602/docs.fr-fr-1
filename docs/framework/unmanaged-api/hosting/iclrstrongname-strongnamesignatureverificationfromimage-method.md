---
title: "Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f312e1eade6de57df9660a349570398d9cd912b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="5b819-102">Méthode ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="5b819-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="5b819-103">Vérifie qu’un assembly qui a déjà été mappé à la mémoire est valide pour la clé publique associée.</span><span class="sxs-lookup"><span data-stu-id="5b819-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b819-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b819-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b819-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b819-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="5b819-106">[in] L’adresse virtuelle relative du manifeste d’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="5b819-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5b819-107">[in] La taille, en octets, de l’image mappée.</span><span class="sxs-lookup"><span data-stu-id="5b819-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="5b819-108">[in] Indicateurs qui influencent le comportement de vérification.</span><span class="sxs-lookup"><span data-stu-id="5b819-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="5b819-109">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="5b819-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="5b819-110">`SN_INFLAG_FORCE_VER`(0 x 00000001) - force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.</span><span class="sxs-lookup"><span data-stu-id="5b819-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="5b819-111">`SN_INFLAG_INSTALL`(0 x 00000002) - Spécifie qu’il s’agit de la première vérification effectuée sur cette image.</span><span class="sxs-lookup"><span data-stu-id="5b819-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="5b819-112">`SN_INFLAG_ADMIN_ACCESS`(0 x 00000004) - Spécifie que le cache autorise l’accès uniquement aux utilisateurs qui ont des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="5b819-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="5b819-113">`SN_INFLAG_USER_ACCESS`(0 x 00000008) - Spécifie que l’assembly est accessible uniquement à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="5b819-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="5b819-114">`SN_INFLAG_ALL_ACCESS`(0 x 00000010) - Spécifie que le cache ne va fournir aucune garantie de restriction d’accès.</span><span class="sxs-lookup"><span data-stu-id="5b819-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="5b819-115">`SN_INFLAG_RUNTIME`(0 x 80000000) - réservé pour le débogage interne.</span><span class="sxs-lookup"><span data-stu-id="5b819-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="5b819-116">[out] Un indicateur pour les données de sortie supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5b819-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="5b819-117">La valeur suivante est prise en charge :</span><span class="sxs-lookup"><span data-stu-id="5b819-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="5b819-118">`SN_OUTFLAG_WAS_VERIFIED`(0 x 00000001) - cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres de Registre.</span><span class="sxs-lookup"><span data-stu-id="5b819-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b819-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5b819-119">Return Value</span></span>  
 <span data-ttu-id="5b819-120">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="5b819-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b819-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b819-121">Requirements</span></span>  
 <span data-ttu-id="5b819-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b819-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b819-123">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5b819-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5b819-124">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b819-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b819-125">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b819-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b819-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b819-126">See Also</span></span>  
 [<span data-ttu-id="5b819-127">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="5b819-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
