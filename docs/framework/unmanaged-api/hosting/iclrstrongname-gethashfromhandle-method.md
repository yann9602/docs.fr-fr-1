---
title: "Méthode ICLRStrongName::GetHashFromHandle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e0f0cc5ba4bb48f5d54427f6e94f72ef8fbd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="3b541-102">Méthode ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="3b541-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="3b541-103">Génère un hachage sur le contenu du fichier qui a le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="3b541-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b541-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b541-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b541-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b541-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="3b541-106">[in] Le handle du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="3b541-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3b541-107">[dans, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="3b541-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3b541-108">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="3b541-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3b541-109">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="3b541-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3b541-110">[in] La taille maximum demandée `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3b541-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3b541-111">[out] La taille, en octets, de retourné `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3b541-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b541-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3b541-112">Return Value</span></span>  
 <span data-ttu-id="3b541-113">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="3b541-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b541-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b541-114">Requirements</span></span>  
 <span data-ttu-id="3b541-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b541-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b541-116">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3b541-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3b541-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b541-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b541-118">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b541-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b541-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b541-119">See Also</span></span>  
 [<span data-ttu-id="3b541-120">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="3b541-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
