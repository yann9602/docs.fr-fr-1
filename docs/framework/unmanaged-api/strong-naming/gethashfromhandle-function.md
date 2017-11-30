---
title: GetHashFromHandle, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromHandle
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromHandle
helpviewer_keywords: GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ccb6d3b50e70d69b706f63be8a783ad6d7f7cdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="9a985-102">GetHashFromHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="9a985-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="9a985-103">Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="9a985-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="9a985-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="9a985-104">This function has been deprecated.</span></span> <span data-ttu-id="9a985-105">Utilisez le [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="9a985-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a985-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a985-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a985-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a985-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="9a985-108">[in] Le handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="9a985-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9a985-109">[dans, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="9a985-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9a985-110">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a985-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9a985-111">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="9a985-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9a985-112">[in] La taille maximum demandée `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9a985-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9a985-113">[out] La taille, en octets, de retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9a985-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a985-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a985-114">Requirements</span></span>  
 <span data-ttu-id="9a985-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a985-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a985-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9a985-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9a985-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a985-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a985-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a985-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a985-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a985-119">See Also</span></span>  
 [<span data-ttu-id="9a985-120">GetHashFromHandle (méthode)</span><span class="sxs-lookup"><span data-stu-id="9a985-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="9a985-121">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="9a985-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
