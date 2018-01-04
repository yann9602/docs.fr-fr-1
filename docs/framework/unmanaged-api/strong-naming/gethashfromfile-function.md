---
title: GetHashFromFile, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFile
helpviewer_keywords: GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="18ffd-102">GetHashFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="18ffd-102">GetHashFromFile Function</span></span>
<span data-ttu-id="18ffd-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="18ffd-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="18ffd-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="18ffd-104">This function has been deprecated.</span></span> <span data-ttu-id="18ffd-105">Utilisez le [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="18ffd-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ffd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18ffd-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18ffd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18ffd-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="18ffd-108">[in] Le nom du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="18ffd-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="18ffd-109">[dans, out] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="18ffd-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="18ffd-110">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="18ffd-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="18ffd-111">Si `piHashAlg` est définie sur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="18ffd-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="18ffd-112">[out] Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="18ffd-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="18ffd-113">[in] La taille maximale de la mémoire tampon qui `pbHash` pointe vers.</span><span class="sxs-lookup"><span data-stu-id="18ffd-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="18ffd-114">[out] La taille, en octets, de retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="18ffd-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18ffd-115">Notes</span><span class="sxs-lookup"><span data-stu-id="18ffd-115">Remarks</span></span>  
 <span data-ttu-id="18ffd-116">Cette fonction est identique à [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), sauf que la spécification de nom de fichier est au format ANSI au lieu d’Unicode.</span><span class="sxs-lookup"><span data-stu-id="18ffd-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ffd-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18ffd-117">Requirements</span></span>  
 <span data-ttu-id="18ffd-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18ffd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ffd-119">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="18ffd-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="18ffd-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18ffd-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18ffd-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18ffd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ffd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18ffd-122">See Also</span></span>  
 [<span data-ttu-id="18ffd-123">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="18ffd-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="18ffd-124">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="18ffd-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="18ffd-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="18ffd-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
