---
title: StrongNameTokenFromPublicKey, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: COM
f1_keywords: StrongNameTokenFromPublicKey
helpviewer_keywords: StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfde09f6383646f24077c3bdc0efa4b31bc50ba0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="01aa4-102">StrongNameTokenFromPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="01aa4-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="01aa4-103">Obtient un jeton représentant une clé publique.</span><span class="sxs-lookup"><span data-stu-id="01aa4-103">Gets a token representing a public key.</span></span> <span data-ttu-id="01aa4-104">Un jeton de nom fort est la forme abrégée d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="01aa4-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="01aa4-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="01aa4-105">This function has been deprecated.</span></span> <span data-ttu-id="01aa4-106">Utilisez le [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="01aa4-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01aa4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01aa4-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01aa4-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01aa4-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="01aa4-109">[in] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="01aa4-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="01aa4-110">[in] La taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="01aa4-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="01aa4-111">[out] Le jeton de nom fort correspondant à la clé passée dans `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="01aa4-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="01aa4-112">Le common language runtime alloue de la mémoire dans lequel retourner le jeton.</span><span class="sxs-lookup"><span data-stu-id="01aa4-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="01aa4-113">L’appelant doit libérer cette mémoire en utilisant la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="01aa4-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="01aa4-114">[out] La taille, en octets, du jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="01aa4-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01aa4-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="01aa4-115">Return Value</span></span>  
 <span data-ttu-id="01aa4-116">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="01aa4-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01aa4-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="01aa4-117">Remarks</span></span>  
 <span data-ttu-id="01aa4-118">Un jeton de nom fort est la forme abrégée d’une clé publique utilisée pour économiser de l’espace lorsque vous stockez des informations de clé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="01aa4-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="01aa4-119">Plus précisément, les jetons de nom fort sont utilisés dans les références d’assembly pour faire référence à l’assembly dépendant.</span><span class="sxs-lookup"><span data-stu-id="01aa4-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="01aa4-120">Si le `StrongNameTokenFromPublicKey` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="01aa4-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01aa4-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01aa4-121">Requirements</span></span>  
 <span data-ttu-id="01aa4-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01aa4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01aa4-123">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="01aa4-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="01aa4-124">**Bibliothèque :** inclus en tant que ressource dans mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="01aa4-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="01aa4-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01aa4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01aa4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01aa4-126">See Also</span></span>  
 [<span data-ttu-id="01aa4-127">StrongNameTokenFromPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="01aa4-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="01aa4-128">StrongNameGetPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="01aa4-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="01aa4-129">PublicKeyBlob (Structure)</span><span class="sxs-lookup"><span data-stu-id="01aa4-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
