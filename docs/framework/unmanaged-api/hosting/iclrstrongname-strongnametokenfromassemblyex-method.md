---
title: "Méthode ICLRStrongName::StrongNameTokenFromAssemblyEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e46216f9e64d76188d60dbfcfc8e5113f2409b07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="17305-102">Méthode ICLRStrongName::StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="17305-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="17305-103">Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique que le jeton représente.</span><span class="sxs-lookup"><span data-stu-id="17305-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17305-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17305-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17305-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17305-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="17305-106">[in] Le chemin d’accès au fichier exécutable portable (PE) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="17305-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="17305-107">[out] Le jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="17305-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="17305-108">[out] La taille, en octets, du jeton de nom fort.</span><span class="sxs-lookup"><span data-stu-id="17305-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="17305-109">[out] La clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="17305-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="17305-110">[out] La taille, en octets, de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="17305-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17305-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="17305-111">Return Value</span></span>  
 <span data-ttu-id="17305-112">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="17305-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17305-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="17305-113">Remarks</span></span>  
 <span data-ttu-id="17305-114">Un jeton de nom fort est la forme abrégée d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="17305-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="17305-115">Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="17305-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="17305-116">Le jeton fait partie du nom fort de l’assembly et peut être lus à partir des métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="17305-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="17305-117">Une fois que la clé est récupérée et le jeton est créé, vous devez appeler la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="17305-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17305-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="17305-118">Requirements</span></span>  
 <span data-ttu-id="17305-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17305-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17305-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="17305-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="17305-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17305-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17305-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17305-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17305-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17305-123">See Also</span></span>  
 [<span data-ttu-id="17305-124">StrongNameTokenFromAssembly (méthode)</span><span class="sxs-lookup"><span data-stu-id="17305-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="17305-125">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="17305-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
