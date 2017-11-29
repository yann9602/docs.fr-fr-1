---
title: "Méthode ICLRStrongName::StrongNameTokenFromPublicKey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84f47fcef7c896b197de410234694c211d07c30b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="cccf9-102">Méthode ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="cccf9-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="cccf9-103">Obtient un jeton qui représente une clé publique.</span><span class="sxs-lookup"><span data-stu-id="cccf9-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="cccf9-104">Un jeton de nom fort est la forme abrégée d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="cccf9-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccf9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cccf9-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cccf9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cccf9-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="cccf9-107">[in] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="cccf9-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="cccf9-108">[in] La taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cccf9-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="cccf9-109">[out] Le jeton de nom fort correspondant à la clé passée dans `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cccf9-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="cccf9-110">Le common language runtime alloue de la mémoire dans lequel retourner le jeton.</span><span class="sxs-lookup"><span data-stu-id="cccf9-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="cccf9-111">L’appelant doit libérer cette mémoire en utilisant la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="cccf9-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="cccf9-112">[out] La taille, en octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="cccf9-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cccf9-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cccf9-113">Return Value</span></span>  
 <span data-ttu-id="cccf9-114">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="cccf9-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cccf9-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="cccf9-115">Remarks</span></span>  
 <span data-ttu-id="cccf9-116">Un jeton de nom fort est la forme abrégée d’une clé publique qui est utilisée pour économiser de l’espace lorsque vous stockez des informations de clé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cccf9-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="cccf9-117">Plus précisément, les jetons de nom fort sont utilisés dans les références d’assembly pour faire référence à l’assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="cccf9-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cccf9-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cccf9-118">Requirements</span></span>  
 <span data-ttu-id="cccf9-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccf9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccf9-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cccf9-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cccf9-121">**Bibliothèque :** inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cccf9-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="cccf9-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccf9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cccf9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cccf9-123">See Also</span></span>  
 [<span data-ttu-id="cccf9-124">StrongNameGetPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="cccf9-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="cccf9-125">PublicKeyBlob (Structure)</span><span class="sxs-lookup"><span data-stu-id="cccf9-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="cccf9-126">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="cccf9-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
