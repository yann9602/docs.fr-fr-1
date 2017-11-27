---
title: StrongNameGetPublicKey, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameGetPublicKey
helpviewer_keywords: StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 243b5f8d94805d8631c7c79f424d9e6434213bb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="ba49f-102">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="ba49f-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="ba49f-103">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="ba49f-104">La paire de clés peut être fournie comme un nom de conteneur de clé dans un fournisseur de services de chiffrement (CSP) ou comme une collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="ba49f-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="ba49f-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-105">This function has been deprecated.</span></span> <span data-ttu-id="ba49f-106">Utilisez le [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="ba49f-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba49f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba49f-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba49f-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba49f-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ba49f-109">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ba49f-110">Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le CSP.</span><span class="sxs-lookup"><span data-stu-id="ba49f-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ba49f-111">Dans ce cas, `StrongNameGetPublicKey` extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="ba49f-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ba49f-112">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="ba49f-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ba49f-113">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="ba49f-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ba49f-114">Aucun autre type de clés n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ba49f-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ba49f-115">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ba49f-116">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="ba49f-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ba49f-117">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `szKeyContainer` est supposé pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="ba49f-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ba49f-118">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ba49f-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ba49f-119">[out] La clé publique BLOB retournée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ba49f-120">Le `ppbPublicKeyBlob` paramètre est allouée par le common language runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ba49f-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ba49f-121">L’appelant doit libérer la mémoire à l’aide de la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="ba49f-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ba49f-122">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="ba49f-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba49f-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ba49f-123">Return Value</span></span>  
 <span data-ttu-id="ba49f-124">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="ba49f-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba49f-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="ba49f-125">Remarks</span></span>  
 <span data-ttu-id="ba49f-126">La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="ba49f-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="ba49f-127">Si le `StrongNameGetPublicKey` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="ba49f-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba49f-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba49f-128">Requirements</span></span>  
 <span data-ttu-id="ba49f-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba49f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba49f-130">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ba49f-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ba49f-131">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba49f-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba49f-132">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba49f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba49f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba49f-133">See Also</span></span>  
 [<span data-ttu-id="ba49f-134">StrongNameGetPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="ba49f-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="ba49f-135">StrongNameTokenFromPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="ba49f-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="ba49f-136">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="ba49f-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="ba49f-137">PublicKeyBlob (Structure)</span><span class="sxs-lookup"><span data-stu-id="ba49f-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
