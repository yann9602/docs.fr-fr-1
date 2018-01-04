---
title: "Méthode ICLRStrongName::StrongNameSignatureGeneration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGeneration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcf872dcd1de34aaade06cf26914a75ae971b85b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="3b9eb-102">Méthode ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="3b9eb-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="3b9eb-103">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b9eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b9eb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b9eb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b9eb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3b9eb-106">[in] Le chemin d’accès au fichier qui contient le manifeste de l’assembly pour lequel la signature de nom fort est générée.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="3b9eb-107">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="3b9eb-108">Si `pbKeyBlob` a la valeur null, `wszKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP).</span><span class="sxs-lookup"><span data-stu-id="3b9eb-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="3b9eb-109">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="3b9eb-110">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="3b9eb-111">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="3b9eb-112">Aucun autre type de clés n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="3b9eb-113">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="3b9eb-114">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="3b9eb-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="3b9eb-115">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `wszKeyContainer` est supposé pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="3b9eb-116">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="3b9eb-117">[out] Pointeur vers l’emplacement auquel le common language runtime retourne la signature.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="3b9eb-118">Si `ppbSignatureBlob` est null, le runtime stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="3b9eb-119">Si `ppbSignatureBlob` est non null, le common language runtime alloue de l’espace dans lequel retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="3b9eb-120">L’appelant doit libérer cet espace à l’aide de la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3b9eb-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="3b9eb-121">[out] La taille, en octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b9eb-122">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3b9eb-122">Return Value</span></span>  
 <span data-ttu-id="3b9eb-123">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="3b9eb-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b9eb-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3b9eb-124">Remarks</span></span>  
 <span data-ttu-id="3b9eb-125">Spécifiez null pour `wszFilePath` pour calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="3b9eb-126">La signature peut être enregistrés directement dans le fichier ou retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="3b9eb-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b9eb-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b9eb-127">Requirements</span></span>  
 <span data-ttu-id="3b9eb-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b9eb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b9eb-129">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3b9eb-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3b9eb-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b9eb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b9eb-131">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b9eb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9eb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b9eb-132">See Also</span></span>  
 [<span data-ttu-id="3b9eb-133">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="3b9eb-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="3b9eb-134">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="3b9eb-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
