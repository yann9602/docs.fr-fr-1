---
title: GetHashFromBlob, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromBlob
helpviewer_keywords: GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 360036cd1578c2845f09f92c09d79e44618abe75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="60f19-102">GetHashFromBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="60f19-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="60f19-103">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="60f19-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="60f19-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="60f19-104">This function has been deprecated.</span></span> <span data-ttu-id="60f19-105">Utilisez le [ICLRStrongName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="60f19-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f19-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f19-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60f19-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60f19-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="60f19-108">[in] Pointeur vers l’adresse du bloc de mémoire à hacher.</span><span class="sxs-lookup"><span data-stu-id="60f19-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="60f19-109">[in] La longueur, en octets, du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="60f19-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="60f19-110">[dans, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="60f19-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="60f19-111">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="60f19-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="60f19-112">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="60f19-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="60f19-113">[in] La taille maximum demandée `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="60f19-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="60f19-114">[out] La taille, en octets, de retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="60f19-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f19-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="60f19-115">Requirements</span></span>  
 <span data-ttu-id="60f19-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f19-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f19-117">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="60f19-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="60f19-118">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60f19-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60f19-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f19-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f19-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60f19-120">See Also</span></span>  
 [<span data-ttu-id="60f19-121">GetHashFromBlob (méthode)</span><span class="sxs-lookup"><span data-stu-id="60f19-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="60f19-122">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="60f19-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
