---
title: "Méthode ICLRStrongName::StrongNameSignatureGenerationEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGenerationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b0527be680ed755366f77593e4dc7e1dea830c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="ad9f9-102">Méthode ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="ad9f9-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="ad9f9-103">Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad9f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad9f9-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad9f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad9f9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ad9f9-106">[in] Le chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort est générée.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="ad9f9-107">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="ad9f9-108">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="ad9f9-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ad9f9-109">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="ad9f9-110">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ad9f9-111">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ad9f9-112">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="ad9f9-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ad9f9-113">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `wszKeyContainer` est supposé pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ad9f9-114">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="ad9f9-115">[out] Pointeur vers l’emplacement auquel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="ad9f9-116">Si `ppbSignatureBlob` est null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="ad9f9-117">Si `ppbSignatureBlob` est non null, le common language runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="ad9f9-118">L’appelant doit libérer cet espace à l’aide de la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ad9f9-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="ad9f9-119">[out] La taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ad9f9-120">[in] Un ou plusieurs des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad9f9-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="ad9f9-121">`SN_SIGN_ALL_FILES`(0 x 00000001) - recalculez tous les hachages pour les modules liés.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="ad9f9-122">`SN_TEST_SIGN`(0 x 00000002) - signature de test de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad9f9-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ad9f9-123">Return Value</span></span>  
 <span data-ttu-id="ad9f9-124">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="ad9f9-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad9f9-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad9f9-125">Remarks</span></span>  
 <span data-ttu-id="ad9f9-126">Spécifiez null pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="ad9f9-127">La signature peut être soit stockée directement dans le fichier, soit retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="ad9f9-128">Si `SN_SIGN_ALL_FILES` est spécifié, mais une clé publique n’est pas incluse (les deux `pbKeyBlob` et `wszFilePath` ont la valeur null), les hachages pour les modules liés sont recalculés, mais l’assembly n’est pas signé de nouveau.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="ad9f9-129">Si `SN_TEST_SIGN` est spécifié, l’en-tête du common language runtime n’est pas modifié pour indiquer que l’assembly est signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ad9f9-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad9f9-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ad9f9-130">Requirements</span></span>  
 <span data-ttu-id="ad9f9-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad9f9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad9f9-132">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ad9f9-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad9f9-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad9f9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad9f9-134">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad9f9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9f9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad9f9-135">See Also</span></span>  
 [<span data-ttu-id="ad9f9-136">StrongNameSignatureGeneration (méthode)</span><span class="sxs-lookup"><span data-stu-id="ad9f9-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="ad9f9-137">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="ad9f9-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
