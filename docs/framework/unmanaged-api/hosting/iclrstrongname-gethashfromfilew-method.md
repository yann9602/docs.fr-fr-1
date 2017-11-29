---
title: "Méthode ICLRStrongName::GetHashFromFileW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc7589e2a977502a3e75a95b8a065f45b8805072
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="88bd5-102">Méthode ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="88bd5-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="88bd5-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="88bd5-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88bd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88bd5-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="88bd5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88bd5-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="88bd5-106">[in] Le nom Unicode du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="88bd5-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="88bd5-107">[dans, out] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="88bd5-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="88bd5-108">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="88bd5-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="88bd5-109">Si `piHashAlg` est définie sur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="88bd5-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="88bd5-110">[out] Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="88bd5-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="88bd5-111">[in] La taille maximale de la mémoire tampon pointée par `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="88bd5-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="88bd5-112">[out] La taille, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="88bd5-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88bd5-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="88bd5-113">Return Value</span></span>  
 <span data-ttu-id="88bd5-114">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="88bd5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88bd5-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="88bd5-115">Remarks</span></span>  
 <span data-ttu-id="88bd5-116">Cette méthode est identique à la [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , à ceci près que le nom de fichier spécification est Unicode et non ANSI.</span><span class="sxs-lookup"><span data-stu-id="88bd5-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88bd5-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="88bd5-117">Requirements</span></span>  
 <span data-ttu-id="88bd5-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88bd5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88bd5-119">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="88bd5-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="88bd5-120">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88bd5-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88bd5-121">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88bd5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bd5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88bd5-122">See Also</span></span>  
 [<span data-ttu-id="88bd5-123">GetHashFromFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="88bd5-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="88bd5-124">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="88bd5-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
