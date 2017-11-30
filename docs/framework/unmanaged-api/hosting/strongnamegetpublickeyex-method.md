---
title: "StrongNameGetPublicKeyEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f39c5c948d43fd0e9387c1cc0319a46d25ec86ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="74d43-102">StrongNameGetPublicKeyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="74d43-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="74d43-103">Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.</span><span class="sxs-lookup"><span data-stu-id="74d43-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d43-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74d43-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74d43-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="74d43-106">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="74d43-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="74d43-107">Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="74d43-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="74d43-108">Dans ce cas, le `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="74d43-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="74d43-109">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="74d43-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="74d43-110">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="74d43-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="74d43-111">Aucun autre type de clés n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="74d43-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="74d43-112">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="74d43-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="74d43-113">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="74d43-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="74d43-114">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `szKeyContainer` est supposé pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="74d43-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="74d43-115">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="74d43-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="74d43-116">[out] La clé publique BLOB retournée.</span><span class="sxs-lookup"><span data-stu-id="74d43-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="74d43-117">Le `ppbPublicKeyBlob` paramètre est allouée par le common language runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="74d43-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="74d43-118">L’appelant doit libérer la mémoire à l’aide de la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="74d43-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="74d43-119">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="74d43-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="74d43-120">[in] Algorithme de hachage de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="74d43-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="74d43-121">Consultez la section Notes pour obtenir la liste de valeurs acceptées.</span><span class="sxs-lookup"><span data-stu-id="74d43-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="74d43-122">[in] Réservé à un usage ultérieur ; valeur par défaut est null.</span><span class="sxs-lookup"><span data-stu-id="74d43-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74d43-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="74d43-123">Return Value</span></span>  
 <span data-ttu-id="74d43-124">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="74d43-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74d43-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="74d43-125">Remarks</span></span>  
 <span data-ttu-id="74d43-126">La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="74d43-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74d43-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="74d43-127">Remarks</span></span>  
 <span data-ttu-id="74d43-128">Le tableau suivant affiche l’ensemble des valeurs acceptées pour la `uHashAlgId` paramètre.</span><span class="sxs-lookup"><span data-stu-id="74d43-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="74d43-129">Nom</span><span class="sxs-lookup"><span data-stu-id="74d43-129">Name</span></span>|<span data-ttu-id="74d43-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="74d43-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="74d43-131">None</span><span class="sxs-lookup"><span data-stu-id="74d43-131">None</span></span>|<span data-ttu-id="74d43-132">0</span><span class="sxs-lookup"><span data-stu-id="74d43-132">0</span></span>|  
|<span data-ttu-id="74d43-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="74d43-133">SHA-1</span></span>|<span data-ttu-id="74d43-134">0 x 8004</span><span class="sxs-lookup"><span data-stu-id="74d43-134">0x8004</span></span>|  
|<span data-ttu-id="74d43-135">SHA-256.</span><span class="sxs-lookup"><span data-stu-id="74d43-135">SHA-256</span></span>|<span data-ttu-id="74d43-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="74d43-136">0x800c</span></span>|  
|<span data-ttu-id="74d43-137">SHA-384.</span><span class="sxs-lookup"><span data-stu-id="74d43-137">SHA-384</span></span>|<span data-ttu-id="74d43-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="74d43-138">0x800d</span></span>|  
|<span data-ttu-id="74d43-139">SHA-512.</span><span class="sxs-lookup"><span data-stu-id="74d43-139">SHA-512</span></span>|<span data-ttu-id="74d43-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="74d43-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74d43-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="74d43-141">Requirements</span></span>  
 <span data-ttu-id="74d43-142">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74d43-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74d43-143">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="74d43-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="74d43-144">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74d43-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74d43-145">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74d43-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d43-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74d43-146">See Also</span></span>  
 [<span data-ttu-id="74d43-147">StrongNameTokenFromPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="74d43-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="74d43-148">PublicKeyBlob (Structure)</span><span class="sxs-lookup"><span data-stu-id="74d43-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="74d43-149">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="74d43-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="74d43-150">StrongNameGetPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="74d43-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
